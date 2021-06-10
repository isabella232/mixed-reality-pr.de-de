---
title: Abhängigkeitsfenster
description: Dokumentation zur Verwendung des Abhängigkeitsfensters im MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: fd17db3f365d8bd97b8cd9c43a6111e2b82a61fe
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647035"
---
# <a name="dependency-window"></a>Abhängigkeitsfenster

In Unity ist es oft schwierig, zu erkennen, welche Ressourcen verwendet werden und was darauf verweist. Die Option "Verweise in Szene suchen" funktioniert hervorragend, wenn Sie sich nur mit der aktuellen Szene befassen, aber was ist mit Ihrem gesamten Unity-Projekt? Hier kann das **Abhängigkeitsfenster** (Assets/MRTK/Tools/DependencyWindow) nützlich sein.

Im Abhängigkeitsfenster wird angezeigt, wie Ressourcen aufeinander verweisen und voneinander abhängig sind. Abhängigkeiten werden berechnet, indem GUIDs in YAML-Projektdateien analysiert werden (Beachten Sie, dass Skript-zu-Skript-Abhängigkeiten nicht berücksichtigt werden).

## <a name="usage"></a>Verwendung

Um das Fenster zu öffnen, wählen Sie **Mixed Reality**  >  **Abhängigkeitsfenster** für  >  **Toolkit-Hilfsprogramme** aus, um das Fenster zu  >   öffnen und automatisch mit dem Erstellen des Abhängigkeitsdiagramms Ihres Projekts zu beginnen. Nachdem das Abhängigkeitsdiagramm erstellt wurde, können Sie Objekte auf der Projektregisterkarte auswählen, um deren Abhängigkeiten zu überprüfen.

![Abhängigkeitsfenster](../images/dependency-window/MRTK_Dependency_Window.png)

Im Fenster werden eine Liste der Ressourcen, von denen das derzeit ausgewählte Medienobjekt abhängt, und eine hierarchische Liste der Davon abhängigen Ressourcen angezeigt. Wenn nichts vom derzeit ausgewählten Medienobjekt abhängt, können Sie es aus Ihrem Projekt löschen (beachten Sie, dass einige Objekte programmgesteuert über APIs wie Shader.Find() geladen werden und möglicherweise nicht vom Abhängigkeitsnachverfolgungs-Objekt abgefangen werden.

Im Fenster kann auch nur eine Liste aller Ressourcen angezeigt werden, auf die keine anderen Ressourcen verweisen und die für den Löschvorgang in Betracht gezogen werden können:

![Abhängigkeitsfenster mit nicht abgeleiteten Ressourcen](../images/dependency-window/MRTK_Dependency_Window_Unreferenced.png)

> [!NOTE]
> Wenn Objekte geändert, hinzugefügt oder entfernt werden, während das Abhängigkeitsfenster verwendet wird, wird empfohlen, das Abhängigkeitsdiagramm für die aktuellsten Ergebnisse zu aktualisieren.
