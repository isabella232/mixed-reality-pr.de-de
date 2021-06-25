---
title: Einrichten der XR-Konfiguration
description: Bleiben Sie über die neuesten Unity XR-Konfigurationsempfehlungen für die Entwicklung von HoloLens-Anwendungen auf dem laufenden.
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Unity
ms.openlocfilehash: d265725caf95379dfa01baa6dad1b7927fbeca5c
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906940"
---
# <a name="setting-up-your-xr-configuration"></a>Einrichten der XR-Konfiguration

Wenn Sie ein neues Unity-Projekt starten, haben Sie drei verschiedene Optionen für die Verarbeitung Ihrer XR-Anforderungen: 
* OpenXR-Plug-In
* Windows XR-Plug-In
* Legacy-XR-Plug-In

[!INCLUDE[](includes/xr/intro.md)]

## <a name="setting-up-your-project-with-mrtk"></a>Einrichten Ihres Projekts mit MRTK

MRTK für Unity bietet ein plattformübergreifendes Eingabesystem, Grundlagenkomponenten und gemeinsame Bausteine für räumliche Interaktionen. MRTK, Version 2, soll die Anwendungsentwicklung für Microsoft HoloLens, für immersive Windows Mixed Reality-Headsets (VR) und für die OpenVR-Plattform beschleunigen. Das Projekt ist darauf ausgerichtet, die Einstiegshürden zum Erstellen von Mixed Reality-Anwendungen zu verringern, und einen Beitrag für die Community auf diesem stetig wachsenden Gebiet zu leisten.

> [!div class="nextstepaction"]
> [Probieren Sie unsere MRTK-Tutorials aus](./tutorials/mr-learning-base-02.md?tabs=winxr)

Weitere Details zu Features finden Sie in der [MRTK-Dokumentation](/windows/mixed-reality/mrtk-unity).

### <a name="using-mrtk-with-openxr-support"></a>Verwenden von MRTK mit OpenXR-Unterstützung

MRTK-Unity Version 2.7 bietet bessere Unterstützung für das Mixed Reality OpenXR-Plug-In.

Öffnen Sie [Mixed Reality Featuretool erneut,](welcome-to-mr-feature-tool.md) um das Mixed Reality Toolkit zu installieren, sofern noch nicht vorhanden. OpenXR-Unterstützung ist im **Foundation-Paket** enthalten.

Weitere ausführliche Informationen zur Migration zu OpenXR finden Sie in der [MRTK-Dokumentation.](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)

> [!NOTE]
> Stellen Sie beim Upgrade von einer früheren Version von MRTK vor **2.5.3** sicher, dass sich die folgende Zeile in der Datei **Assets/MixedRealityToolkit.Generated/link.xml** befindet:
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> Diese Zeile wird standardmäßig hinzugefügt, wenn Sie mit MRTK 2.5.4 oder neuer begonnen haben.

## <a name="manual-setup-without-mrtk"></a>Manuelle Einrichtung ohne MRTK

Microsoft und die Community haben OpenSource-Tools wie das [Mixed Reality Toolkit (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) erstellt, mit denen die WMR-Umgebung automatisch eingerichtet wird, aber viele Entwickler möchten ihre Erfahrungen von Grund auf neu erstellen.

[!INCLUDE[](includes/xr/manual-setup.md)]