---
ms.openlocfilehash: ce1f02bd2846cadc4e970fef738fb4b46bc3a09f10742b820a0998491c590c80
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115204283"
---
# <a name="all-platforms"></a>[Alle Plattformen](#tab/all)

### <a name="enabling-hp-motion-controller-plugin"></a>Aktivieren des HP Motion Controller-Plug-Ins 

Das Interaktionsprofil und die Controllerzuordnungen befinden sich im HP Motion Controller-Plug-In, das aktiviert werden muss, um die Controllerzuordnungen für das Eingabesystem von Unreal verfügbar zu machen.

![Aktivieren des OpenXRHPController-Plug-Ins](../images/reverb-g2-img-01.png)

# <a name="steamvr"></a>[SteamVR](#tab/steamvr)

### <a name="configuring-startup-and-hmdpluginpriority"></a>Konfigurieren von Startup und HMDPluginPriority

Die Eingabe in Unreal mithilfe von SteamVR hat einige Unterschiede.  Stellen Sie beim Einrichten des Projekts zunächst sicher, dass es das neue Eingabesystem von SteamVR verwendet, indem Sie **vr hinzufügen. SteamVR.EnableVRInput=1** zum **Abschnitt Start** in **Engine/Config/ConsoleVariables.ini.**  Diese Ini befindet sich im Installationsverzeichnis der Engine, nicht im Projektverzeichnis.

![Aktualisieren der Startkonfiguration](../images/reverb-g2-img-07.png)

Das HP Motion Controller-Plug-In aktiviert OpenXR.  Wenn Sie OpenXR nicht verwenden, müssen Sie die HMDPluginPriority von SteamVR in BaseEngine.ini im gleichen Verzeichnis wie ConsoleVariables.ini.  Ändern Sie den Wert von "SteamVR" so, dass er größer als der OpenXRHMD-Wert ist.

![Aktualisieren der HMDPluginPriority-Konfiguration](../images/reverb-g2-img-08.png)


