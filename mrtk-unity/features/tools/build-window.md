---
title: Fenster „Build“ (Erstellen)
description: Dokumentation zur Verwendung des Buildfensters in MRTK für Unity.
author: cre8ivepark
ms.author: dongpark
ms.date: 04/06/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Build, Buildfenster, Tools
ms.openlocfilehash: b0b2bb1d06a561f5f647d01145fe88f562c53017
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176149"
---
# <a name="build-window"></a>Fenster „Build“ (Erstellen)
![Erstellen & Bereitstellungsflows](images/MRTK_BuildWindow0.png)

Das MRTK-Buildfenster erleichtert das Erstellen & Bereitstellen Ihrer MRTK-Unity Projekte. Mit einem einzigen Klick auf die Schaltfläche können Sie ein Unity-Projekt erstellen und Visual Studio projektmappe(. SLN), UWP-App-Paket(. APPX), und installieren Sie das App-Paket auf dem Gerät. 


## <a name="unity-build-options"></a>Unity-Buildoptionen
![Buildfenster – Unity-Buildoptionen 1](images/MRTK_BuildWindow1.png)

Diese Szenen stammen aus der Unity Build Einstellungen. Sie können den Zielgerätetyp über das Dropdownmenü ändern.

## <a name="appx-build-options"></a>Appx-Buildoptionen
![Buildfenster – Appx-Buildoptionen 2](images/MRTK_BuildWindow2.png)

Auf dieser Registerkarte wird die Konfiguration für die Visual Studio Projektmappe angezeigt. Aktivieren Sie die Option **Eingabefunktion anverfolgen,** um die Eyetracking-Eingabefunktion von HoloLens 2 zu aktivieren. 

Sie können die GLB-Datei im Feld **3D-App Startprogramm Modell** für das benutzerdefinierte 3D-App-Startfeldsymbol zuweisen. Weitere Informationen finden Sie unter Entwurfsrichtlinie für [3D-App-Starter.](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance)

Standardmäßig wird **automatisches Inkrement** in den Versionierungsoptionen aktiviert. AppX-Versionen werden automatisch erhöht.


## <a name="deploy-options"></a>Bereitstellungsoptionen
![Buildfenster – Bereitstellungsoptionen 3](images/MRTK_BuildWindow3.png)

Auf dieser Registerkarte können Sie eine Verbindung mit dem Gerät herstellen, indem Sie Benutzername und Kennwort für die Geräteportal eingeben. 

Unten auf der Seite finden Sie eine Liste der app-Pakete, die erstellt wurden. 

