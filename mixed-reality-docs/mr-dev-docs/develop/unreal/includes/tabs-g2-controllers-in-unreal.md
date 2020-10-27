---
ms.openlocfilehash: dcbeceb4cbe6b87cd6458afa789f9e09abaf7f3d
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638732"
---
# <a name="all-platforms"></a>[Alle Plattformen](#tab/all)

### <a name="enabling-hp-motion-controller-plugin"></a>Aktivieren von HP Motion Controller Plugin 

Das Interaktions Profil und die Controller Zuordnungen befinden sich im HP Motion Controller-Plug-in, das aktiviert werden muss, um die Controller Zuordnungen für das Eingabe System von Unreal verfügbar zu machen.

![Aktivieren des openxrhpcontroller-Plug-ins](../images/reverb-g2-img-01.png)

# <a name="steamvr"></a>[SteamVR](#tab/steamvr)

### <a name="configuring-startup-and-hmdpluginpriority"></a>Konfigurieren von Start und hmdpluginpriority

Eingaben in Unreal mit steamvr haben einige Unterschiede.  Vergewissern Sie sich beim Einrichten des Projekts zunächst, dass das neue Eingabe System von steamvr verwendet wird, indem Sie VR hinzufügen **. Steamvr. enablevrinput = 1** bis zum **Start** Abschnitt in **Engine/config/ConsoleVariables.ini** .  Diese ini befindet sich im Installationsverzeichnis der Engine, nicht im Projektverzeichnis.

![Aktualisieren der Startkonfiguration](../images/reverb-g2-img-07.png)

Das HP Motion Controller-Plug-in aktiviert openxr.  Wenn Sie openxr nicht verwenden, müssen Sie den hmdpluginpriority-Wert von "steamvr" in BaseEngine.ini in demselben Verzeichnis wie ConsoleVariables.ini bearbeiten.  Ändern Sie den Wert von "steamvr" in einen höheren Wert als den openxrhmd-Wert.

![Aktualisieren der hmdpluginpriority-Konfiguration](../images/reverb-g2-img-08.png)


