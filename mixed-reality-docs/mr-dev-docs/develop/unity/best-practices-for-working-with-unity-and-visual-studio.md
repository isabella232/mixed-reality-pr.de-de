---
title: Bewährte Methoden für Unity und Visual Studio
description: Tipps und Tricks, um den Workflow für die Erstellung einer gemischten Reality-Anwendung mit Unity und Visual Studio zu optimieren.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: bereitstellen, Unity, Visual Studio, hololens, hololens 2, immersives Headset, bewährte Methoden, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, UWP, Visual Studio-Tools Windows SDK
ms.openlocfilehash: 6940382af605c28686cec862cf2d9b6cb8411387
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583463"
---
# <a name="best-practices-for-working-with-unity-and-visual-studio"></a>Bewährte Methoden für das Arbeiten mit Unity und Visual Studio

Wenn Sie eine gemischte Reality-Anwendung mit Unity erstellen, müssen Sie zwischen Unity und Visual Studio wechseln, um das App-Paket zu erstellen und in hololens oder einem immersiven Headset bereitzustellen. Standardmäßig sind zwei Instanzen von Visual Studio erforderlich: eine Instanz zum Ändern von Unity-Skripts und eine andere zum Bereitstellen auf dem Gerät und Debuggen. Mithilfe der folgenden Anweisungen können Sie eine einzelne Visual Studio-Instanz entwickeln, um die Häufigkeit des Exports von Unity-Projekten zu verringern und das Debuggen zu verbessern.

## <a name="improving-iteration-time"></a>Verbessern der Iterations Zeit

Unterstützung für .NET-Skript-Back-End in Unity wird in Unity 2018 als veraltet markiert und in Unity 2019 und höher entfernt. Daher wird empfohlen, zu [IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html)zu wechseln. Sie können jedoch längere Buildzeiten von Unity zu Visual Studio erleben. Um eine schnellere Iteration zu verbessern, richten Sie Ihre Umgebung für optimale Kompilierungs Ergebnisse ein:

1) Verwenden Sie das inkrementelle erstellen, indem Sie Ihr Projekt jedes Mal in demselben Verzeichnis erstellen, indem Sie die vordefinierten Dateien wieder verwenden.
2) Antischadsoftwarescans für Ihr Projekt & Buildordner deaktivieren
   - Öffnen Sie **Viren & Bedrohungsschutz** unter Ihrer Windows 10-Einstellungs-APP.
   - Wählen Sie unter **Viren & Bedrohungsschutz Einstellungen** die Option **Einstellungen verwalten** .
   - Wählen Sie im Abschnitt **Ausschlüsse** die Option **Ausschlüsse hinzufügen oder entfernen**
   - Wählen Sie **Ausschluss hinzufügen** aus, und wählen Sie den Ordner mit Ihrem Unity-Projekt Code und Buildausgaben aus
3) Verwenden eines SSD zum entwickeln

Weitere Informationen finden Sie in [Optimierungs Buildzeiten für IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html) . Überprüfen Sie außerdem das [Debugging auf dem IL2CPP-Skript-Back-End](https://docs.unity3d.com/Manual/windowsstore-debugging-il2cpp.html).

Sie sollten die [Visual Studio-Erweiterung *unityscriptanalyzer*](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer)installieren. Dieses Tool analysiert Ihre Unity c#-Skripts für Code, der auf optimierte Weise geschrieben werden kann.

## <a name="visual-studio-tools-for-unity"></a>Visual Studio Tools für Unity

Download [Visual Studio-Tools für Unity](/visualstudio/cross-platform/getting-started-with-visual-studio-tools-for-unity)

**Vorteile von Visual Studio-Tools für Unity**
* Debuggen Sie den Unity-im-Editor-Wiedergabemodus in Visual Studio, indem Sie Haltepunkte einfügen, Variablen und komplexe Ausdrücke auswerten.
* Verwenden Sie den Unity-Projekt-Explorer, um das Skript mit derselben Hierarchie zu suchen, die in Unity angezeigt wird.
* Holen Sie sich die Unity-Konsole direkt in Visual Studio.
* Mithilfe von Assistenten können Sie schnell Skripts erstellen oder zu ihnen navigieren.

## <a name="expose-c-class-variables-for-easy-tuning"></a>C#-Klassen Variablen für die einfache Optimierung verfügbar machen

Es gibt zwei Möglichkeiten, Klassen Variablen verfügbar zu machen. Die empfohlene Vorgehensweise besteht darin, das Attribut [serializefield] den privaten Variablen hinzuzufügen. Auf serialisierte Felder kann über den Editor zugegriffen werden, aber nicht Programm gesteuert verfügbar gemacht werden.  Die andere Möglichkeit besteht darin, c#-Klassen Variablen öffentlich zu machen, um Sie in der Benutzeroberfläche des Editors verfügbar zu machen. 

Beide Ansätze ermöglichen es, Variablen während der Wiedergabe in-Editor leicht zu optimieren. Dies ist besonders nützlich für die Optimierung von Interaktions Eigenschaften.

## <a name="regenerate-uwp-visual-studio-solutions-after-windows-sdk-or-unity-upgrade"></a>Neugenerieren von Visual Studio-Projektmappen nach Windows SDK oder Unity-Upgrade

UWP-Visual Studio-Projektmappen, die in die Quell Code Verwaltung eingecheckt werden, können nach dem Upgrade auf eine neue Windows SDK oder Unity-Engine veraltet werden. Sie können veraltete Lösungen auflösen, nachdem Sie eine neue UWP-Lösung aus Unity aufgebaut und Unterschiede zu der eingecheckten Lösung zusammengeführt haben.

## <a name="use-text-format-assets-for-easy-comparison-of-content-changes"></a>Verwenden von Textformaten zum einfachen Vergleichen von Inhalts Änderungen

Durch das Speichern von Medienobjekten im Textformat wird das Überprüfen von Änderungen der Inhalts Änderung in Visual Studio vereinfacht. Sie können Assets im Textformat speichern, indem Sie **> Projekteinstellungen bearbeiten >-Editor bearbeiten** und den **assetserialisierungsmodus** ändern, um **Text zu erzwingen**. Das Zusammenführen von Text-assetdateiänderungen ist jedoch fehleranfällig und wird nicht empfohlen. Daher sollten Sie in der Quell Code Verwaltung exklusive binäre Auschecken aktivieren.

## <a name="see-also"></a>Weitere Informationen
- [Visual Studio Tools für Unity](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)
- [Optimieren von Buildzeiten für IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html)
- [*Unityscriptanalyzer* Visual Studio-Erweiterung](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer)