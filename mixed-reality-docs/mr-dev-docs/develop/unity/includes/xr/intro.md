---
ms.openlocfilehash: d39f6032eaf9a59ca52a6e7ae9b8e4d227175738
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906941"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

Das Mixed Reality OpenXR-Plug-In ist **die Empfehlung** von Microsoft für Unity 2020 LTS oder höher. Da neue Features in Zukunft entwickelt werden, werden sie in Zukunft nur noch in das OpenXR-Plug-In Mixed Reality enthalten sein.

Das Mixed Reality OpenXR-Plug-In unterstützt AR Foundation 4.0 vollständig und stellt ARPlaneManager- und ARRaycastManager-Implementierungen zur Verfügung. Auf diese Weise können Sie Raycastcode schreiben, der sich dann über HoloLens 2 und ARCore/ARKit-Smartphones und -Tablets erstreckt.

### <a name="prerequisites"></a>Voraussetzungen 

* Neueste [Tools für HoloLens 2 Entwicklung](../../../install-the-tools.md?tabs=unity#installation-checklist)
* Neueste Version von Unity 2020.3 LTS (wir empfehlen 2020.3.8f1 oder höher)

### <a name="minimum-versions"></a>Mindestversionen

Die Anweisungen auf dieser Seite richten Sie mit den neuesten und größten Unity- und OpenXR-Anforderungen ein, die unten aufgeführt sind:

* Neuestes Unity OpenXR-Plug-In (wir empfehlen 1.2 oder höher)
* Neueste Mixed Reality OpenXR-Plug-In, (wir empfehlen Version 1.0.0 oder höher)
* **(Optional)** Neuestes MRTK (wir empfehlen Version 2.7 oder höher)
* **(Optional)** Neuestes Universal Render Pipeline-Paket (wir empfehlen Version 10.5.1 oder höher)

<!-- ![Screenshot of the open xr unity basic sample running on a HoloLens](../../images/openxr-example.png) -->

> [!NOTE]
> Wenn Sie VR-Anwendungen auf einem Windows-PC erstellen, ist Mixed Reality OpenXR-Plug-In nicht unbedingt erforderlich. Sie sollten das Plug-In jedoch installieren, wenn Sie die Controllerzuordnung für HP Reverb G2-Controller anpassen oder Apps erstellen, die sowohl auf HoloLens 2- als auch auf VR-Headsets funktionieren.

# <a name="windows-xr"></a>[Windows XR](#tab/windowsxr)

Microsoft empfiehlt nicht die Verwendung des Windows XR-Plug-Ins für neue Projekte in Unity 2020.

Wenn Sie jedoch Unity 2019 verwenden und AR Foundation 2.0 für die Kompatibilität mit ARCore/ARKit-Geräten benötigen, ermöglicht dieses Plug-In diese Unterstützung.

> [!IMPORTANT]
> Die Verwendung dieses Plug-Ins in Unity 2019 unterstützt azure Spatial Anchors. 

# <a name="legacy-xr"></a>[Legacy-XR](#tab/legacy)

Wenn Sie noch unity 2019 oder früher verwenden, empfiehlt Microsoft die Verwendung der älteren integrierten XR-Unterstützung. Das Windows XR-Plug-In ist zwar in Unity 2019 funktionsfähig, wird jedoch nicht empfohlen, da Azure Spatial Anchors nicht unterstützt wird.