---
ms.openlocfilehash: ca3589364fb27c3f8087572113f09e48d30e087e
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394574"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

Das Mixed Reality OpenXR-Plug-In ist **die Empfehlung von Microsoft** für Unity 2020 LTS oder höher. Da neue Features in Zukunft entwickelt werden, werden sie in Zukunft nur noch im Mixed Reality OpenXR-Plug-Ins enthalten sein.

Das Mixed Reality OpenXR-Plug-In unterstützt AR Foundation 4.0 vollständig und stellt ARPlaneManager- und ARRaycastManager-Implementierungen bereit. Dadurch können Sie raycasting-Code schreiben, der sich dann über HoloLens 2 und ARCore/ARKit-Smartphones und -Tablets erstreckt.

### <a name="prerequisites"></a>Voraussetzungen 

* Neueste [Tools für HoloLens 2 Entwicklung](/windows/mixed-reality/develop/install-the-tools?tabs=unity#installation-checklist)
* Neueste Unity 2020.3 LTS(wir empfehlen 2020.3.8f1 oder höher)

### <a name="minimum-versions"></a>Mindestversionen

Die Anweisungen auf dieser Seite richten Sie mit den neuesten und besten Unity- und OpenXR-Anforderungen ein, die unten aufgeführt sind:

* Neuestes Unity OpenXR-Plug-In (wir empfehlen 1.2 oder höher)
* Neueste Mixed Reality OpenXR-Plug-In(wir empfehlen Version 1.0.0 oder höher)
* **(Optional)** Neuestes MRTK(wir empfehlen Version 2.7 oder höher)
* **(Optional)** Neuestes Universelles Renderpipelinepaket (wir empfehlen Version 10.5.1 oder höher)

<!-- ![Screenshot of the open xr unity basic sample running on a HoloLens](../../images/openxr-example.png) -->

> [!NOTE]
> Wenn Sie VR-Anwendungen auf einem Windows-PC erstellen, ist das Mixed Reality OpenXR-Plug-In nicht unbedingt erforderlich. Sie sollten das Plug-In jedoch installieren, wenn Sie die Controllerzuordnung für HP Reverb G2-Controller anpassen oder Apps erstellen, die sowohl auf HoloLens 2- als auch auf VR-Headsets funktionieren.

# <a name="windows-xr"></a>[Windows XR](#tab/windowsxr)

Microsoft empfiehlt nicht die Verwendung des Windows XR-Plug-Ins für neue Projekte in Unity 2020.

Wenn Sie jedoch Unity 2019 verwenden und AR Foundation 2.0 für die Kompatibilität mit ARCore-/ARKit-Geräten benötigen, ermöglicht dieses Plug-In diese Unterstützung.

> [!IMPORTANT]
> Die Verwendung dieses Plug-Ins in Unity 2019 unterstützt azure Spatial Anchors nicht. 

# <a name="legacy-xr"></a>[Legacy-XR](#tab/legacy)

Wenn Sie noch unity 2019 oder früher verwenden, empfiehlt Microsoft die Verwendung der älteren integrierten XR-Unterstützung. Das Windows XR-Plug-In ist zwar in Unity 2019 funktionsfähig, wird jedoch nicht empfohlen, da Azure Spatial Anchors nicht unterstützt wird.