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
# <a name="dependency-window"></a><span data-ttu-id="27738-104">Abhängigkeitsfenster</span><span class="sxs-lookup"><span data-stu-id="27738-104">Dependency window</span></span>

<span data-ttu-id="27738-105">In Unity ist es oft schwierig, zu erkennen, welche Ressourcen verwendet werden und was darauf verweist.</span><span class="sxs-lookup"><span data-stu-id="27738-105">In Unity, it is often difficult to gleam which assets are being used, and what is referencing them.</span></span> <span data-ttu-id="27738-106">Die Option "Verweise in Szene suchen" funktioniert hervorragend, wenn Sie sich nur mit der aktuellen Szene befassen, aber was ist mit Ihrem gesamten Unity-Projekt?</span><span class="sxs-lookup"><span data-stu-id="27738-106">The "Find References in Scene" option works great when you are only concerned with the current scene, but what about your entire Unity project?</span></span> <span data-ttu-id="27738-107">Hier kann das **Abhängigkeitsfenster** (Assets/MRTK/Tools/DependencyWindow) nützlich sein.</span><span class="sxs-lookup"><span data-stu-id="27738-107">This is where the **Dependency Window** (Assets/MRTK/Tools/DependencyWindow) can be useful.</span></span>

<span data-ttu-id="27738-108">Im Abhängigkeitsfenster wird angezeigt, wie Ressourcen aufeinander verweisen und voneinander abhängig sind.</span><span class="sxs-lookup"><span data-stu-id="27738-108">The Dependency Window displays how assets reference and depend on each other.</span></span> <span data-ttu-id="27738-109">Abhängigkeiten werden berechnet, indem GUIDs in YAML-Projektdateien analysiert werden (Beachten Sie, dass Skript-zu-Skript-Abhängigkeiten nicht berücksichtigt werden).</span><span class="sxs-lookup"><span data-stu-id="27738-109">Dependencies are calculated by parsing guids within project YAML files (note, script to script dependencies are not considered).</span></span>

## <a name="usage"></a><span data-ttu-id="27738-110">Verwendung</span><span class="sxs-lookup"><span data-stu-id="27738-110">Usage</span></span>

<span data-ttu-id="27738-111">Um das Fenster zu öffnen, wählen Sie **Mixed Reality**  >  **Abhängigkeitsfenster** für  >  **Toolkit-Hilfsprogramme** aus, um das Fenster zu  >   öffnen und automatisch mit dem Erstellen des Abhängigkeitsdiagramms Ihres Projekts zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="27738-111">To open the window, select **Mixed Reality** > **Toolkit** > **Utilities** > **Dependency Window** which will open the window and automatically begin building your project's dependency graph.</span></span> <span data-ttu-id="27738-112">Nachdem das Abhängigkeitsdiagramm erstellt wurde, können Sie Objekte auf der Projektregisterkarte auswählen, um deren Abhängigkeiten zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="27738-112">Once the dependency graph is built, you can select assets in the project tab to inspect their dependencies.</span></span>

![Abhängigkeitsfenster](../images/dependency-window/MRTK_Dependency_Window.png)

<span data-ttu-id="27738-114">Im Fenster werden eine Liste der Ressourcen, von denen das derzeit ausgewählte Medienobjekt abhängt, und eine hierarchische Liste der Davon abhängigen Ressourcen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="27738-114">The window displays a list of assets that the currently selected asset depends on, and a hierarchical list of assets that depend on it.</span></span> <span data-ttu-id="27738-115">Wenn nichts vom derzeit ausgewählten Medienobjekt abhängt, können Sie es aus Ihrem Projekt löschen (beachten Sie, dass einige Objekte programmgesteuert über APIs wie Shader.Find() geladen werden und möglicherweise nicht vom Abhängigkeitsnachverfolgungs-Objekt abgefangen werden.</span><span class="sxs-lookup"><span data-stu-id="27738-115">If nothing depends on the currently selected asset, you can consider deleting it from your project (note that some assets are loaded programmatically via APIs like Shader.Find() and may not be caught by the dependency tracker).</span></span>

<span data-ttu-id="27738-116">Im Fenster kann auch nur eine Liste aller Ressourcen angezeigt werden, auf die keine anderen Ressourcen verweisen und die für den Löschvorgang in Betracht gezogen werden können:</span><span class="sxs-lookup"><span data-stu-id="27738-116">The window can also display just a list of all assets which are not referenced by any other assets and could be considered for deletion:</span></span>

![Abhängigkeitsfenster mit nicht abgeleiteten Ressourcen](../images/dependency-window/MRTK_Dependency_Window_Unreferenced.png)

> [!NOTE]
> <span data-ttu-id="27738-118">Wenn Objekte geändert, hinzugefügt oder entfernt werden, während das Abhängigkeitsfenster verwendet wird, wird empfohlen, das Abhängigkeitsdiagramm für die aktuellsten Ergebnisse zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="27738-118">If assets are modified, added, or removed while the dependency window is in use, it is advised to refresh the dependency graph for the most "up to date" results.</span></span>
