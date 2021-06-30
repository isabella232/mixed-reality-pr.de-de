---
title: Auswählen einer Unity-Version und eines XR-Plug-Ins
description: Bleiben Sie über die neuesten Unity- und XR-Plug-In-Empfehlungen für die HoloLens-Anwendungsentwicklung auf dem Laufenden.
author: hferrone
ms.author: v-hferrone
ms.date: 06/24/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Unity
ms.openlocfilehash: 11f930f014ff579db1f8845d52b7a2d65dd85d6b
ms.sourcegitcommit: 4ea9ba1ca1cde426b016111c4176a4b0a9c17553
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2021
ms.locfileid: "113080697"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a>Auswählen einer Unity-Version und eines XR-Plug-Ins

Wir empfehlen derzeit die **Installation von Unity 2020.3 LTS mit dem neuesten Mixed Reality OpenXR-Plug-In** für Mixed Reality Entwicklung, aber Sie können auch Apps mit anderen Unity-Konfigurationen erstellen.

## <a name="unity-20203-lts-recommended"></a>Unity 2020.3 LTS (empfohlen)

Die aktuelle empfohlene Unity-Konfiguration von Microsoft für HoloLens 2 und Windows Mixed Reality Entwicklung ist **Unity 2020.3 LTS mit dem neuesten Mixed Reality OpenXR-Plug-In.** Sie MÜSSEN Unity Patch Release 2020.3.8f1 oder höher verwenden, um bekannte Leistungsprobleme mit früheren Builds von 2020.3 zu vermeiden.

> [!IMPORTANT]
> Unity 2020 unterstützt keine Zielgruppenadressierung für HoloLens (1. Generation). Diese Headsets werden in **[Unity 2019 LTS](#unity-20194-lts)** mit legacy-integriertem XR für den gesamten Lebenszyklus von Unity 2019 LTS bis Mitte 2022 weiterhin unterstützt.
>
> [!NOTE]
> Azure Remote Rendering wurde noch kein aktualisiertes Release veröffentlicht, das Unity 2020 unterstützt.
>
> Wenn Ihr Unity-Projekt Azure Remote Rendering verwendet, wird empfohlen, das Upgrade Ihres Projekts auf Unity 2020 abzuwarten, bis ein aktualisiertes Paket verfügbar ist.

Der beste Weg, um Unity zu installieren und zu verwalten, ist über <a href="https://unity3d.com/get-unity/download" target="_blank">Unity Hub</a>. Öffnen Sie nach der Installation Unity Hub:

1. Wählen Sie die Registerkarte **Installationen** und dann **HINZUFÜGEN** aus.
2. Wählen Sie Unity 2020.3 LTS aus, und klicken Sie auf **Weiter.**

![Unity-Hub in der neuen Version](images/unity-hub-img-01.png)

3. Überprüfen Sie die folgenden Komponenten unter **"Plattformen".**
    * **Buildunterstützung für Universelle Windows-Plattform**
    * **Windows-Buildunterstützung (IL2CPP)**

![Unity: Option „Buildunterstützung für Universelle Windows-Plattform“](../images/Unity_Install_Option_UWP.png)

4. Wenn Sie Unity ohne diese Optionen installiert haben, können Sie sie über das Menü **"Module hinzufügen"** in Unity Hub hinzufügen:

![Unity: Option „Windows-Buildunterstützung“](../images/Unity_Install_Option_UWP2.png)

> [!div class="nextstepaction"]
> [Verwenden des OpenXR-Plug-Ins](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=openxr)

> [!NOTE]
> Wir empfehlen die Verwendung von OpenXR für alle neuen Projekte, Unity 2020.3 LTS unterstützt jedoch auch das [Windows XR-Plug-In](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=windowsxr). Dieses Plug-In wird vollständig unterstützt, obwohl es keine neuen Features wie AR Foundation 4.0-Unterstützung erhält.

## <a name="unity-20194-lts"></a>Unity 2019.4 LTS

Wenn Sie Unity 2019 verwenden müssen, können Sie **Unity 2019 LTS mit legacy-integriertem XR** verwenden. Klicken Sie hier, um mit legacy-integriertem XR in Unity 2019.4 LTS zu beginnen:

> [!div class="nextstepaction"]
> [Einrichten von Legacy-integriertem XR](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=legacy)

> [!NOTE]
> Unity hat die legacy-integrierte XR-Unterstützung ab Unity 2019 als veraltet erklärt.  Während Unity 2019 ein neues XR-Plug-In-Framework bietet, empfiehlt Microsoft diesen Pfad in Unity 2019 aufgrund von Azure Spatial Anchors Inkompatibilitäten mit AR Foundation 2 derzeit nicht.  In Unity 2020 wird Azure Spatial Anchors im XR-Plug-In-Framework unterstützt.

Wenn Sie Apps für HoloLens (1. Generation) entwickeln, werden diese Headsets in Unity 2019 LTS mit legacy-integriertem XR für den gesamten Lebenszyklus von Unity 2019 LTS bis Mitte 2022 weiterhin unterstützt.

## <a name="unity-20211"></a>Unity 2021.1

Wenn Sie frühe **Unity 2021.1-Builds** ausprobieren, sollten Sie mit dem **OpenXR-Plug-In** fortschreiten, da das Windows XR-Plug-In dort veraltet ist.  Ab Unity 2021.2 ist das OpenXR-Plug-In der einzige Pfad für Mixed Reality Entwicklung, da das Windows XR-Plug-In nicht mehr unterstützt wird.

## <a name="unity-20184-lts"></a>Unity 2018.4 LTS

Wenn Sie bereits über ein Projekt mit Unity 2018.4 LTS verfügen, wird Ihre Unity-Engine nach der Veröffentlichung 2 Jahre lang unterstützt.  Unity 2018 LTS wird im Spring 2021 das Ende des Diensts erreichen.
