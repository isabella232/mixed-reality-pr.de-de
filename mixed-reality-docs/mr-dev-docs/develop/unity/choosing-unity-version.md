---
title: Auswählen einer Unity-Version und eines XR-Plug-Ins
description: Bleiben Sie über die neuesten Unity- und XR-Plug-In-Empfehlungen für die Entwicklung von HoloLens-Anwendungen auf dem laufenden.
author: hferrone
ms.author: v-hferrone
ms.date: 05/27/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Unity
ms.openlocfilehash: 1f658c0e69091ce0aaeb37b7f427e57f060c3fb2
ms.sourcegitcommit: 62e5909b837c9c7ecedd040164f2308868db4723
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2021
ms.locfileid: "111741922"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a>Auswählen einer Unity-Version und eines XR-Plug-Ins

Es wird derzeit empfohlen, **Unity 2020.3 LTS** mit dem neuesten Mixed Reality OpenXR-Plug-In für die Mixed Reality-Entwicklung zu installieren. Sie können aber auch Apps mit anderen Unity-Konfigurationen erstellen.

## <a name="unity-20203-lts-recommended"></a>Unity 2020.3 LTS (empfohlen)

Die derzeit empfohlene Unity-Konfiguration von Microsoft für HoloLens 2- und Windows Mixed Reality-Entwicklung ist **Unity 2020.3 LTS** mit dem neuesten Mixed Reality OpenXR-Plug-In.

> [!IMPORTANT]
> Unity 2020 unterstützt holoLens (1. Generation) nicht. Diese Headsets werden in **[Unity 2019 LTS](#unity-20194-lts)** mit integriertem Legacy-XR für den gesamten Lebenszyklus von Unity 2019 LTS bis Mitte 2022 weiterhin unterstützt.

Das Mixed Reality OpenXR-Plug-In unterstützt AR Foundation 4.0 vollständig und stellt ARPlaneManager- und ARRaycastManager-Implementierungen zur Verfügung. Auf diese Weise können Sie Treffertestcode schreiben, der sich dann über HoloLens 2 und ARCore/ARKit-Smartphones und -Tablets erstreckt.

Der beste Weg, um Unity zu installieren und zu verwalten, ist über <a href="https://unity3d.com/get-unity/download" target="_blank">Unity Hub</a>. Wenn sie installiert ist, öffnen Sie Unity Hub:

1. Wählen Sie die **Registerkarte Installs (Installationen)** und dann **ADD (HINZUFÜGEN) aus.**
2. Wählen Sie Unity 2020.3 LTS aus, und klicken Sie auf **Weiter.**

![Neue Version des Unity-Hubs](images/unity-hub-img-01.png)

3. Überprüfen Sie die folgenden Komponenten unter **"Plattformen".**
    * **Buildunterstützung für Universelle Windows-Plattform**
    * **Windows-Buildunterstützung (IL2CPP)**

![Unity: Option „Buildunterstützung für Universelle Windows-Plattform“](../images/Unity_Install_Option_UWP.png)

4. Wenn Sie Unity ohne diese Optionen installiert haben, können Sie diese über das Menü **"Module hinzufügen"** im Unity-Hub hinzufügen:

![Unity: Option „Windows-Buildunterstützung“](../images/Unity_Install_Option_UWP2.png)

> [!div class="nextstepaction"]
> [Verwenden des OpenXR-Plug-Ins](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=openxr)

> [!NOTE]
> Es wird zwar empfohlen, OpenXR für alle neuen Projekte zu verwenden, Unity 2020.3 LTS unterstützt jedoch auch das **[Windows XR-Plug-In](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=windowsxr)**. Bekannte Probleme, die sich auf die Hologrammstabilität und andere Features auf HoloLens 2 auswirken:
>
> * Holographic App-Remotinganwendungen, die Universelle Windows-Plattform Buildziel verwenden, funktionieren nicht.
> * Das Unity-Grafikaufträgesystem ist standardmäßig aktiviert, obwohl es nicht mit HoloLens-Projekten kompatibel ist.

## <a name="unity-20194-lts"></a>Unity 2019.4 LTS

Wenn Sie Unity 2019 verwenden müssen, können Sie **Unity 2019 LTS mit integriertem Legacy-XR verwenden.** Klicken Sie hier, um mit der älteren integrierten XR in Unity 2019.4 LTS zu beginnen:

> [!div class="nextstepaction"]
> [Einrichten von legacy-integriertem XR](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=legacy)

> [!NOTE]
> Unity hat die integrierte Legacy-XR-Unterstützung seit Unity 2019 als veraltet bezeichnet.  Unity 2019 bietet zwar ein neues XR-Plug-In-Framework, Microsoft empfiehlt diesen Pfad in Unity 2019 jedoch aufgrund von Azure Spatial Anchors-Inkompatibilitäten mit AR Foundation 2 nicht.  In Unity 2020 wird Azure Spatial Anchors im XR-Plug-In-Framework unterstützt.

Wenn Sie Apps für HoloLens (1. Generation) entwickeln, werden diese Headsets in Unity 2019 LTS mit integriertem Legacy-XR für den gesamten Lebenszyklus von Unity 2019 LTS bis Mitte 2022 weiterhin unterstützt.

## <a name="unity-20211"></a>Unity 2021.1

Wenn Sie frühe **Unity 2021.1-Builds** ausprobieren, sollten Sie mit dem **OpenXR-Plug-In** vorankommen, da das Windows XR-Plug-In dort veraltet ist.  Ab Unity 2021.2 ist das OpenXR-Plug-In der einzige Pfad für die Mixed Reality-Entwicklung, da das Windows XR-Plug-In nicht mehr unterstützt wird.

## <a name="unity-20184-lts"></a>Unity 2018.4 LTS

Wenn Sie bereits über ein Projekt mit Unity 2018.4 LTS verfügen, wird Ihre Unity-Engine nach der Veröffentlichung zwei Jahre lang weiterhin unterstützt.  Unity 2018 LTS erreicht das Dienstende im Januar 2021.
