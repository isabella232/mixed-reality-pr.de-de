---
title: MRTK-Buildfenster
description: Dokumentation zur Verwendung des Buildfensters in MRTK für Unity.
author: cre8ivepark
ms.author: dongpark
ms.date: 04/06/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Build, Buildfenster, Tools
ms.openlocfilehash: 00ccbc5cfbb3b034771585a1263c624309b08465
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196853"
---
# <a name="build-window"></a>Fenster „Build“ (Erstellen)
![Erstellen & Bereitstellungsablauf](images/MRTK_BuildWindow0.png)

Mit dem Buildfenster des MRTK können Sie ganz einfach & Ihre MRTK-Unity bereitstellen. Mit einem einzigen Klick auf eine Schaltfläche können Sie ein Unity-Projekt erstellen und Visual Studio generieren(. SLN), UWP-App-Paket(. APPX), und installieren Sie das App-Paket auf dem Gerät. 


## <a name="unity-build-options"></a>Unity-Buildoptionen
![Buildfenster – Unity-Buildoptionen 1](images/MRTK_BuildWindow1.png)

Diese Szenen sind aus den Unity-Buildeinstellungen. Sie können den Typ des Zielgeräts über das Dropdownmenü ändern.

## <a name="appx-build-options"></a>Appx-Buildoptionen
![Buildfenster – Appx-Buildoptionen 2](images/MRTK_BuildWindow2.png)

Auf dieser Registerkarte wird die Konfiguration für die Visual Studio angezeigt. Aktivieren Sie HoloLens 2 Eingabefunktion zum Anvingen, um die Eingabefunktion für die Blickverfolgung **zu** aktivieren. 

Sie können die GLB-Datei im **Feld 3D-App-Startfeld Modell** für benutzerdefiniertes 3D-App-Startfeld zuweisen. Weitere Informationen [finden Sie unter Designrichtlinie für das 3D-App-Startfeld.](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance)

Standardmäßig ist **automatisches Inkrement** in den Versionsoptionen aktiviert. AppX-Versionen werden automatisch erhöht.


## <a name="deploy-options"></a>Bereitstellungsoptionen
![Buildfenster – Bereitstellungsoptionen 3](images/MRTK_BuildWindow3.png)

Auf dieser Registerkarte können Sie eine Verbindung mit dem Gerät herstellen, indem Sie Benutzername und Kennwort für die Geräteportal eingeben. 

Unten auf der Seite finden Sie eine Liste der app-Pakete, die erstellt wurden. 

