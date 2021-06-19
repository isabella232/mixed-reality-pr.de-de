---
title: Auswählen einer Unity-Version und eines XR-Plug-Ins
description: Bleiben Sie über die neuesten Unity- und XR-Plug-In-Empfehlungen für die Entwicklung von HoloLens-Anwendungen auf dem laufenden.
author: hferrone
ms.author: v-hferrone
ms.date: 06/18/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Unity
ms.openlocfilehash: 452692b1be98459cc242833149b1cfd91f0f4d4a
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394416"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a>Auswählen einer Unity-Version und eines XR-Plug-Ins

Es wird derzeit empfohlen, **Unity 2019.4 LTS** zu installieren und ältere integrierte XR-Daten für die Mixed Reality-Entwicklung zu verwenden. Sie können aber auch Apps mit anderen Unity-Konfigurationen erstellen.

## <a name="unity-20194-lts-recommended"></a>Unity 2019.4 LTS (empfohlen)

Die derzeit empfohlene Unity-Konfiguration von Microsoft für die HoloLens 2- und Windows Mixed Reality-Entwicklung ist **Unity 2019.4 LTS mit integrierter Legacy-XR-Unterstützung.**

Die beste Möglichkeit zum Installieren und Verwalten von Unity ist der <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity Hub]</a>. Wenn sie installiert ist, öffnen Sie Unity Hub:

1. Wählen Sie die **Registerkarte Installs (Installationen)** und dann **ADD (HINZUFÜGEN) aus.**
2. Wählen Sie Unity 2019.4 LTS aus, und klicken Sie auf **Weiter.**

![Neue Version des Unity-Hubs](images/unity-hub-img-2019.png)

3. Überprüfen Sie die folgenden Komponenten unter **"Plattformen".**
    * **Buildunterstützung für Universelle Windows-Plattform** 
    * **Windows-Buildunterstützung (IL2CPP)**

![Unity: Option „Buildunterstützung für Universelle Windows-Plattform“](images/Unity_Install_Option_UWP_2019.png)

4. Wenn Sie Unity ohne diese Optionen installiert haben, können Sie diese über das Menü **"Module hinzufügen"** in Unity Hub hinzufügen:

![Unity: Option „Windows-Buildunterstützung“](images/Unity_Install_Option_UWP2_2019.png)

Klicken Sie hier, um mit der älteren integrierten XR in Unity 2019.4 LTS zu beginnen:

> [!div class="nextstepaction"]
> [Einrichten von legacy-integriertem XR](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=legacy)

> [!NOTE]
> Unity hat die integrierte Legacy-XR-Unterstützung ab Unity 2019 als veraltet bezeichnet.  Unity 2019 bietet zwar ein neues XR-Plug-In-Framework, Microsoft empfiehlt diesen Pfad in Unity 2019 jedoch aufgrund von Azure Spatial Anchors-Inkompatibilitäten mit AR Foundation 2 nicht.  In Unity 2020 wird Azure Spatial Anchors im XR-Plug-In-Framework unterstützt.

Wenn Sie Apps für HoloLens (1. Generation) entwickeln, werden diese Headsets in Unity 2019 LTS mit integriertem Legacy-XR für den gesamten Lebenszyklus von Unity 2019 LTS bis Mitte 2022 weiterhin unterstützt.

## <a name="unity-20203-lts"></a>Unity 2020.3 LTS 

Wenn Sie **Unity 2020.3 LTS** verwenden, ist die aktuelle Empfehlung von Microsoft die neueste Version Mixed Reality **OpenXR-Plug-Ins.** Sie MÜSSEN Unity Patch Release 2020.3.8f1 oder höher verwenden, um bekannte Leistungsprobleme mit früheren 2020.3-Builds zu vermeiden.

Das Mixed Reality OpenXR-Plug-In unterstützt AR Foundation 4.0 vollständig und stellt ARPlaneManager- und ARRaycastManager-Implementierungen zur Verfügung. Auf diese Weise können Sie Treffertestcode schreiben, der sich dann über HoloLens 2 und ARCore/ARKit-Smartphones und -Tablets erstreckt.

Es gibt jedoch bekannte Probleme, die Unity 2020 LTS-Projekte betreffen:

* Die Universal Rendering Pipeline (URP) 10.5.0 oder älter hat Leistungsbeend auf HoloLens 2 Geräten.

Wenn Sie sich entscheiden, noch heute ein neues Projekt in Unity 2020 zu starten, sollten Sie in den kommenden Wochen unbedingt nach den aktualisierten Unity-Builds und URP-Paketen suchen, bevor Sie Ihre App versenden.  Dadurch wird sichergestellt, dass Ihre Benutzer die richtige Hologrammstabilität haben.

> [!div class="nextstepaction"]
> [Verwenden des OpenXR-Plug-Ins](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=openxr)

## <a name="unity-20211"></a>Unity 2021.1

Wenn Sie frühe **Unity 2021.1-Builds** ausprobieren, sollten Sie mit dem **OpenXR-Plug-In** weiterkommen, da das Windows XR-Plug-In dort veraltet ist.  Ab Unity 2021.2 ist das OpenXR-Plug-In der einzige Pfad für die Mixed Reality-Entwicklung, da das Windows XR-Plug-In nicht mehr unterstützt wird.

## <a name="unity-20184-lts"></a>Unity 2018.4 LTS

Wenn Sie bereits über ein Projekt mit Unity 2018.4 LTS verfügen, wird Ihre Unity-Engine nach der Veröffentlichung zwei Jahre lang weiterhin unterstützt.  Unity 2018 LTS erreicht das Ende des Diensts im Januar 2021.