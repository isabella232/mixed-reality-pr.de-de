---
title: Abhängigkeitsfenster
description: Dokumentation zur Verwendung des Abhängigkeitsfensters im MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 590476add6904f76081630c4416184bea9f694ab
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176661"
---
# <a name="dependency-window"></a>Abhängigkeitsfenster

In Unity ist es oft schwierig, zu erkennen, welche Ressourcen verwendet werden und was darauf verweist. Die Option "Verweise in Szene suchen" funktioniert hervorragend, wenn Sie sich nur mit der aktuellen Szene befassen, aber was ist mit Ihrem gesamten Unity-Projekt? Hier kann das **Abhängigkeitsfenster** (Assets/MRTK/Tools/DependencyWindow) nützlich sein.

Im Abhängigkeitsfenster wird angezeigt, wie Ressourcen aufeinander verweisen und voneinander abhängig sind. Abhängigkeiten werden berechnet, indem GUIDs in YAML-Projektdateien analysiert werden (Beachten Sie, dass Skript-zu-Skript-Abhängigkeiten nicht berücksichtigt werden).

## <a name="usage"></a>Verwendung

Um das Fenster zu öffnen, wählen Sie **Mixed Reality**  >  **Abhängigkeitsfenster** für  >  **Toolkit-Hilfsprogramme** aus, um das Fenster zu  >   öffnen und automatisch mit dem Erstellen des Abhängigkeitsdiagramms Ihres Projekts zu beginnen. Nachdem das Abhängigkeitsdiagramm erstellt wurde, können Sie Objekte auf der Projektregisterkarte auswählen, um deren Abhängigkeiten zu überprüfen.

![Abhängigkeitsfenster](../images/dependency-window/MRTK_Dependency_Window.png)

Das Fenster zeigt eine Liste der Ressourcen an, von denen das aktuell ausgewählte Medienobjekt abhängt, sowie eine hierarchische Liste von Ressourcen, die davon abhängig sind. Wenn nichts vom derzeit ausgewählten Medienobjekt abhängt, können Sie es aus Ihrem Projekt löschen (beachten Sie, dass einige Ressourcen programmgesteuert über APIs wie Shader.Find() geladen werden und möglicherweise nicht vom Abhängigkeitsnachverfolgungs-Objekt abgefangen werden.

Das Fenster kann auch nur eine Liste aller Ressourcen anzeigen, auf die keine anderen Ressourcen verweisen und die für den Löschvorgang in Betracht gezogen werden können:

![Abhängigkeitsfenster mit nicht zurückgeleiteten Ressourcen](../images/dependency-window/MRTK_Dependency_Window_Unreferenced.png)

> [!NOTE]
> Wenn Objekte geändert, hinzugefügt oder entfernt werden, während das Abhängigkeitsfenster verwendet wird, wird empfohlen, das Abhängigkeitsdiagramm für die aktuellsten Ergebnisse zu aktualisieren.
