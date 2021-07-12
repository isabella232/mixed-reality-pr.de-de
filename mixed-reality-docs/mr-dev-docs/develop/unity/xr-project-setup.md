---
title: Einrichten ihrer XR-Konfiguration
description: Bleiben Sie über die neuesten Unity XR-Konfigurationsempfehlungen für HoloLens Anwendungsentwicklung auf dem Laufenden.
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Unity
ms.openlocfilehash: d2904b9ea4771286b7091a8d5b7c599fcbd1244a
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603715"
---
# <a name="setting-up-your-xr-configuration"></a>Einrichten ihrer XR-Konfiguration

Nachdem Sie [eine Unity-Version ausgewählt](choosing-unity-version.md)haben, besteht der nächste Schritt darin, die XR-Konfiguration auszuwählen, die Sie zum Erstellen Ihrer Mixed Reality-App verwenden:

## <a name="choosing-an-xr-configuration"></a>Auswählen einer XR-Konfiguration

Wenn Sie ein neues Unity-Projekt starten, verfügen Sie über verschiedene XR-Konfigurationen, die Sie auswählen können: das **Mixed Reality OpenXR-Plug-In,** das **Windows XR-Plug-In** und **legacy built-in XR**.

[!INCLUDE[](includes/xr/intro.md)]

## <a name="setting-up-your-project-with-mrtk"></a>Einrichten Ihres Projekts mit MRTK

Die einfachste Möglichkeit, Ihr Unity-Projekt für Mixed Reality einzurichten, ist das Mixed Reality Toolkit (MRTK).  MRTK für Unity ist ein plattformübergreifendes Open-Source-Development Kit, das die Erstellung beeindruckender Mixed Reality-Anwendungen erleichtert.

![MRTK](../../design/images/MRTK_UX_Hero.png)

MRTK bietet ein plattformübergreifendes Eingabesystem, Grundlagenkomponenten und gemeinsame Bausteine für räumliche Interaktionen.  Mit MRTK Version 2 können Sie ihre Anwendungsentwicklung für Microsoft HoloLens, Windows Mixed Reality immersive Headsets (VR) und viele andere VR/AR-Geräte beschleunigen. Das Projekt zielt darauf ab, Einstiegsbarrieren zu verringern, sodass jeder Mixed Reality-Anwendungen erstellen und bei jedem Wachstum zur Community beitragen kann.

[!INCLUDE[](includes/xr/mrtk-next-step.md)]

Weitere Informationen zum Mixed Reality Toolkit finden Sie in der [MRTK-Dokumentation.](/windows/mixed-reality/mrtk-unity)

## <a name="manual-setup-without-mrtk"></a>Manuelle Einrichtung ohne MRTK

Während Microsoft und die Community Open Source-Tools wie das [Mixed Reality Toolkit (MRTK)](/windows/mixed-reality/mrtk-unity) erstellt haben, mit denen Ihre Umgebung automatisch für Mixed Reality eingerichtet wird, möchten einige Entwickler ihre Erfahrungen möglicherweise von Grund auf erstellen.

[!INCLUDE[](includes/xr/manual-setup.md)]