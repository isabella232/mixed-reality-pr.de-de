---
ms.openlocfilehash: eaa2651a22fd5b2b601493845d507aeda6745f1a
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603713"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

Das Mixed Reality OpenXR-Plug-In ist **die Empfehlung** von Microsoft für **Unity 2020 LTS** oder höher. Da neue Features in Zukunft entwickelt werden, werden sie in Zukunft nur noch in das OpenXR-Plug-In Mixed Reality enthalten sein.

Das Mixed Reality OpenXR-Plug-In unterstützt AR Foundation 4.0 vollständig und stellt ARPlaneManager- und ARRaycastManager-Implementierungen zur Verfügung. Auf diese Weise können Sie Raycastcode schreiben, sobald er sich über HoloLens 2 und ARCore/ARKit-Smartphones und -Tablets erstreckt.

### <a name="prerequisites"></a>Voraussetzungen 

* Neueste [Tools für HoloLens 2 Entwicklung](../../../install-the-tools.md?tabs=unity#installation-checklist)
* Neueste Unity 2020.3 LTS: Version 2020.3.8f1 oder höher

### <a name="recommended-package-versions"></a>Empfohlene Paketversionen

Die Anweisungen auf dieser Seite richten Sie mit den grundlegenden Unity OpenXR-Paketen ein, die zum Bereitstellen HoloLens 2 oder Windows Mixed Reality erforderlich sind:

* Unity OpenXR-Plug-In: Version 1.2 oder höher
* Mixed Reality OpenXR-Plug-In: Version 1.0.0 oder höher

Wenn Sie die folgenden Pakete in Ihrem Projekt verwenden, müssen Sie sicherstellen, dass Sie mindestens die unten aufgeführten Mindestversionen verwenden:

* MRTK: Version 2.7.2 oder höher
* AR Foundation: Version 4.1.1 oder höher
* Universal Render Pipeline (URP): Version 10.5.1 oder höher
* Azure Spatial Anchors: Version 2.10 oder höher
* Azure Remote Rendering: Version 1.0.15 oder höher

> [!NOTE]
> Wenn Sie VR-Anwendungen auf einem Windows PC erstellen, ist Mixed Reality OpenXR-Plug-In nicht zwingend erforderlich. Sie sollten das Plug-In jedoch installieren, wenn Sie Eingabebindungen für HP Reverb G2-Controller einrichten oder Apps erstellen, die sowohl auf HoloLens 2- als auch auf VR-Headsets funktionieren.

# <a name="windows-xr"></a>[Windows Xr](#tab/windowsxr)

Microsoft empfiehlt nicht die Verwendung des Windows XR-Plug-Ins für neue Projekte in Unity 2020.  Stattdessen sollten Sie das OpenXR Mixed Reality-Plug-In verwenden.

Wenn Sie jedoch Unity 2019 verwenden und AR Foundation 2.0 für die Kompatibilität mit ARCore/ARKit-Geräten benötigen, ermöglicht dieses Plug-In diese Unterstützung.

> [!IMPORTANT]
> Die Verwendung dieses Plug-Ins in Unity 2019 ist nicht mit Azure Spatial Anchors.

# <a name="legacy-xr"></a>[Legacy-XR](#tab/legacy)

Wenn Sie noch unity **2019** oder früher verwenden, empfiehlt Microsoft die Verwendung der **älteren integrierten XR-Unterstützung.**

Das Windows XR-Plug-In ist zwar in Unity 2019 funktionsfähig, wird jedoch nicht empfohlen, da dieses Plug-In nicht mit Azure Spatial Anchors unter Unity 2019 kompatibel ist.

Wenn Sie ein neues Projekt starten, empfiehlt es sich, [stattdessen Unity 2020](../../choosing-unity-version.md) zu installieren und das OpenXR Mixed Reality-Plug-In zu verwenden.