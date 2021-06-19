---
title: Einrichten der XR-Konfiguration
description: Bleiben Sie über die neuesten Unity XR-Konfigurationsempfehlungen für die HoloLens-Anwendungsentwicklung auf dem Laufenden.
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Unity
ms.openlocfilehash: df7c5039c6cdcfa1e39dc96f0829611dd5209772
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394564"
---
# <a name="setting-up-your-xr-configuration"></a>Einrichten der XR-Konfiguration

Wenn Sie ein neues Unity-Projekt starten, stehen Ihnen drei verschiedene Optionen zur Verfügung, um Ihre XR-Anforderungen zu erfüllen: 
* OpenXR-Plug-In
* Windows XR-Plug-In
* Legacy-XR-Plug-In

[!INCLUDE[](includes/xr/intro.md)]

## <a name="setting-up-your-project-with-mrtk"></a>Einrichten Ihres Projekts mit MRTK

MRTK für Unity bietet ein plattformübergreifendes Eingabesystem, Grundlagenkomponenten und gemeinsame Bausteine für räumliche Interaktionen. MRTK, Version 2, soll die Anwendungsentwicklung für Microsoft HoloLens, für immersive Windows Mixed Reality-Headsets (VR) und für die OpenVR-Plattform beschleunigen. Das Projekt ist darauf ausgerichtet, die Einstiegshürden zum Erstellen von Mixed Reality-Anwendungen zu verringern, und einen Beitrag für die Community auf diesem stetig wachsenden Gebiet zu leisten.

> [!div class="nextstepaction"]
> [Probieren Sie unsere MRTK-Tutorials aus](/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02?tabs=winxr)

Weitere Details zu Features finden Sie in der [MRTK-Dokumentation](/windows/mixed-reality/mrtk-unity).

### <a name="using-mrtk-with-openxr-support"></a>Verwenden von MRTK mit OpenXR-Unterstützung

MRTK-Unity Release 2.7 bietet bessere Unterstützung für das Mixed Reality OpenXR-Plug-In.

Öffnen Sie das [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) erneut, um das Mixed Reality Toolkit zu installieren, sofern noch nicht erfolgt. OpenXR-Unterstützung ist im **Foundation-Paket** enthalten.

[Ausführlichere Informationen zur Migration zu OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)finden Sie in der MRTK-Dokumentation.

> [!NOTE]
> Stellen Sie beim Upgrade von einer früheren Version von MRTK vor **2.5.3** sicher, dass sich die folgende Zeile in der Datei **Assets/MixedRealityToolkit.Generated/link.xml** befindet:
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> Diese Zeile wird standardmäßig hinzugefügt, wenn Sie mit MRTK 2.5.4 oder neuer gestartet haben.

## <a name="manual-setup-without-mrtk"></a>Manuelle Einrichtung ohne MRTK

Während Microsoft und die Community OpenSource-Tools wie das [Mixed Reality Toolkit (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) erstellt haben, mit denen die WMR-Umgebung automatisch eingerichtet wird, möchten viele Entwickler ihre Erfahrungen von Grund auf erstellen.

[!INCLUDE[](includes/xr/manual-setup.md)]
