---
title: Bewährte Methoden für Unity und Visual Studio
description: Tipps und Tricks, um den Workflow zum Erstellen einer Mixed Reality-Anwendung mit Unity und Visual Studio zu optimieren.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Bereitstellen, Unity, Visual Studio, HoloLens, HoloLens 2, immersives Headset, bewährte Methoden, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, UWP, Visual Studio-Tools, Windows SDK
ms.openlocfilehash: cc1ef6448ebabd1729dbe056cdccc40ab7444466701094cc942f2a20fbe81a65
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115186880"
---
# <a name="best-practices-for-working-with-unity-and-visual-studio"></a>Bewährte Methoden für das Arbeiten mit Unity und Visual Studio

Wenn Sie eine Mixed Reality-Anwendung mit Unity erstellen, müssen Sie zwischen Unity und Visual Studio wechseln, um das App-Paket für HoloLens oder ein immersives Headset zu erstellen und bereitzustellen. Standardmäßig sind zwei Instanzen von Visual Studio erforderlich: eine Instanz zum Ändern von Unity-Skripts und eine andere für die Bereitstellung auf dem Gerät und das Debuggen. Mit den folgenden Anweisungen können Sie die Entwicklung mit einer einzelnen Visual Studio-Instanz durchführen, um die Häufigkeit des Exports von Unity-Projekten zu reduzieren und die Debugerfahrung zu verbessern.

## <a name="improving-iteration-time"></a>Verbessern der Iterationszeit

Die Unterstützung für das .NET-Skript-Back-End in Unity wurde in Unity 2018 veraltet und ab Unity 2019 und mehr entfernt. Daher wird empfohlen, zu [IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html)zu wechseln. Es können jedoch längere Buildzeiten von Unity bis Visual Studio auftreten. Um eine schnellere Iteration zu erzielen, richten Sie Ihre Umgebung für optimale Kompilierungsergebnisse ein:

1) Verwenden Sie inkrementelles Erstellen, indem Sie Ihr Projekt jedes Mal im gleichen Verzeichnis erstellen und die vorgefertigten Dateien dort wiederverwenden.
2) Deaktivieren von Antischadsoftwarescans für Ihr Projekt & Buildordner
   - Öffnen **Sie Virus & Threat Protection** unter Ihrer App mit den Windows 10-Einstellungen.
   - Wählen Sie unter **Virenschutzeinstellungen & die Option** **Einstellungen verwalten** aus.
   - Wählen Sie im Abschnitt **Ausschlüsse** die Option **Ausschlüsse hinzufügen oder entfernen** aus.
   - Wählen **Sie Ausschluss hinzufügen** aus, und wählen Sie den Ordner mit Ihrem Unity-Projektcode und den Buildausgaben aus.
3) Verwenden einer SSD zum Erstellen

Weitere Informationen finden Sie unter [Optimieren der Buildzeiten für IL2CPP.](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html) Lesen Sie auch [Debugging on IL2CPP Scripting Back-End (Debuggen auf IL2CPP-Skripterstellungs-Back-End).](https://docs.unity3d.com/Manual/windowsstore-debugging-il2cpp.html)

Erwägen Sie die Installation von [ *UnityScriptAnalyzer* Visual Studio Erweiterung](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer). Dieses Tool analysiert Ihre Unity C#-Skripts auf Code, der optimiert geschrieben werden kann.

## <a name="visual-studio-tools-for-unity"></a>Visual Studio Tools für Unity

Herunterladen [Visual Studio-Tools für Unity](/visualstudio/cross-platform/getting-started-with-visual-studio-tools-for-unity)

**Vorteile von Visual Studio-Tools für Unity**
* Debuggen Sie den Wiedergabemodus von Unity im Editor aus Visual Studio, indem Sie Haltepunkte setzen, Variablen und komplexe Ausdrücke auswerten.
* Verwenden Sie den Unity-Project-Explorer, um Ihr Skript mit derselben Hierarchie zu suchen, die von Unity angezeigt wird.
* Sie können die Unity-Konsole direkt in Visual Studio abrufen.
* Verwenden Sie Assistenten, um schnell Skripts zu erstellen oder zu diesen zu navigieren.

## <a name="expose-c-class-variables-for-easy-tuning"></a>Verfügbar machen von C#-Klassenvariablen zur einfachen Optimierung

Es gibt zwei Möglichkeiten, Klassenvariablen verfügbar zu machen. Die empfohlene Methode ist das Hinzufügen des Attributs [SerializeField] zu Ihren privaten Variablen. Auf serialisierte Felder kann über den Editor zugegriffen werden, aber nicht programmgesteuert.  Die andere Option besteht darin, C#-Klassenvariablen öffentlich zu machen, um sie auf der Benutzeroberfläche des Editors verfügbar zu machen. 

Beide Ansätze ermöglichen das einfache Optimieren von Variablen während der Wiedergabe im Editor. Dies ist besonders nützlich für die Optimierung von Interaktionseigenschaften.

## <a name="regenerate-uwp-visual-studio-solutions-after-windows-sdk-or-unity-upgrade"></a>Neugenerieren von UWP-Visual Studio-Lösungen nach Windows SDK oder Unity-Upgrade

UWP-Visual Studio Lösungen, die in die Quellcodeverwaltung eingecheckt werden, können nach dem Upgrade auf ein neues Windows SDK oder eine Unity-Engine veraltet sein. Sie können veraltete Lösungen nach auflösen, indem Sie eine neue UWP-Lösung aus Unity erstellen und Unterschiede in der eingecheckten Lösung zusammenführen.

## <a name="use-text-format-assets-for-easy-comparison-of-content-changes"></a>Verwenden von Textformatressourcen für den einfachen Vergleich von Inhaltsänderungen

Das Speichern von Ressourcen im Textformat erleichtert das Überprüfen von Inhaltsänderungsvergleichen in Visual Studio. Sie können Objekte im Textformat speichern, indem **Sie > Project Einstellungen > Editor bearbeiten** auswählen und den **Medienobjektserialisierungsmodus** in **Text erzwingen** ändern. Das Zusammenführen von Änderungen an Textdateien ist jedoch fehleranfällig und wird nicht empfohlen. Aktivieren Sie daher exklusive binäre Auscheckfunktionen in Ihrer Quellcodeverwaltung.

## <a name="see-also"></a>Weitere Informationen
- [Visual Studio Tools für Unity](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)
- [Optimieren der Buildzeiten für IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html)
- [*UnityScriptAnalyzer* Visual Studio-Erweiterung](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer)