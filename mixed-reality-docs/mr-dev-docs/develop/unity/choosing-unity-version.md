---
title: Auswählen einer Unity-Version und eines XR-Plug-Ins
description: Bleiben Sie über die neuesten Unity- und XR-Plug-In-Empfehlungen für HoloLens Anwendungsentwicklung auf dem Laufenden.
author: hferrone
ms.author: v-hferrone
ms.date: 06/24/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Unity
ms.openlocfilehash: 7d22ccee301345352ae384f8b237415f925bbd254e0923197130caf48540c171
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210865"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a>Auswählen einer Unity-Version und eines XR-Plug-Ins

Es wird derzeit empfohlen, **Unity 2020.3 LTS** mit dem neuesten Mixed Reality OpenXR-Plug-In für die Mixed Reality-Entwicklung zu installieren. Sie können aber auch Apps mit anderen Unity-Konfigurationen erstellen.

## <a name="unity-20203-lts-recommended"></a>Unity 2020.3 LTS (empfohlen)

Die derzeit von Microsoft empfohlene Unity-Konfiguration für HoloLens 2- und Windows Mixed Reality-Entwicklung ist **Unity 2020.3 LTS** mit dem neuesten Mixed Reality OpenXR-Plug-In. Sie **müssen** Unity Patch Release 2020.3.8f1 oder höher verwenden, um bekannte Leistungsprobleme mit früheren 2020.3-Builds zu vermeiden.

> [!IMPORTANT]
> Unity 2020 unterstützt keine Zielgruppenadressierung HoloLens (1. Generation). Diese Headsets werden in **[Unity 2019 LTS](#unity-20194-lts)** mit integriertem Legacy-XR für den gesamten Lebenszyklus von Unity 2019 LTS bis Mitte 2022 weiterhin unterstützt.

Die beste Möglichkeit zum Installieren und Verwalten von Unity ist der **Unity Hub:**

1. Installieren <a href="https://unity3d.com/get-unity/download" target="_blank">**Sie Unity Hub**</a>.
2. Wählen Sie die **Registerkarte Installs** (Installationen) und dann **Add (Hinzufügen) aus.**
3. Wählen **Sie Unity 2020.3 LTS aus,** und klicken Sie auf **Weiter.**

![Unity Hub: Installieren einer neuen Version](images/unity-hub-img-01.png)

4. Überprüfen Sie die folgenden Komponenten unter **"Plattformen":**
    * **Buildunterstützung für Universelle Windows-Plattform**
    * **Windows-Buildunterstützung (IL2CPP)**

![Unity: Option „Buildunterstützung für Universelle Windows-Plattform“](../images/Unity_Install_Option_UWP.png)

5. Wenn Sie Unity zuvor ohne diese Optionen installiert haben, können Sie diese über das Menü **"Module hinzufügen"** in Unity Hub hinzufügen:

![Unity: Option „Windows-Buildunterstützung“](../images/Unity_Install_Option_UWP2.png)

Nachdem Sie Unity 2020.3 installiert haben, beginnen Sie mit dem Erstellen eines Projekts oder Aktualisieren eines vorhandenen Projekts mithilfe des Mixed Reality OpenXR-Plug-Ins:

> [!div class="nextstepaction"]
> [Einrichten Ihres Projekts mit dem OpenXR-Plug-In](xr-project-setup.md?tabs=openxr)

> [!NOTE]
> Es wird zwar empfohlen, OpenXR für alle neuen Projekte zu verwenden, Unity 2020.3 LTS unterstützt jedoch auch das [Windows XR-Plug-In](xr-project-setup.md?tabs=windowsxr). Dieses Plug-In wird vollständig unterstützt, obwohl es keine neuen Features wie AR Foundation 4.0-Unterstützung erhält.

## <a name="unity-20194-lts"></a>Unity 2019.4 LTS

Wenn Sie Unity 2019 verwenden müssen, können Sie **Unity 2019 LTS mit integriertem Legacy-XR verwenden.** Klicken Sie hier, um mit der älteren integrierten XR in Unity 2019.4 LTS zu beginnen:

> [!div class="nextstepaction"]
> [Einrichten Ihres Projekts mit legacy-integriertem XR](xr-project-setup.md?tabs=legacy)

> [!NOTE]
> Unity hat die integrierte Legacy-XR-Unterstützung ab Unity 2019 als veraltet bezeichnet.  Unity 2019 bietet zwar ein neues XR-Plug-In-Framework, Microsoft empfiehlt diesen Pfad in Unity 2019 jedoch aufgrund von Azure Spatial Anchors-Inkompatibilitäten mit AR Foundation 2 nicht.  In Unity 2020 wird Azure Spatial Anchors im XR-Plug-In-Framework unterstützt.

Wenn Sie Apps für HoloLens (1. Generation) entwickeln, werden diese Headsets in Unity 2019 LTS mit integriertem Legacy-XR für den gesamten Lebenszyklus von Unity 2019 LTS bis Mitte 2022 weiterhin unterstützt.

## <a name="unity-20212"></a>Unity 2021.2

Wenn Sie frühe **Unity 2021.2-Builds** ausprobieren, beginnen Sie mit dem Mixed Reality [**OpenXR-Plug-In.**](xr-project-setup.md?tabs=openxr) Das OpenXR-Plug-In ist der einzige Pfad für die Mixed Reality-Entwicklung in Unity 2021.2 und höher, da unity 2021.1 die endgültige Unity-Version zur Unterstützung des Windows XR-Plug-Ins war.

## <a name="unity-20184-lts"></a>Unity 2018.4 LTS

Unity 2018.4 LTS hat das Ende des zwei jahre dauernden Long-Term-Supportfensters von Unity erreicht und empfängt keine Updates mehr von Unity, obwohl Ihre Projekte weiterhin ausgeführt werden.

Wenn Sie über ein Unity 2018-Projekt verfügen, sollten Sie eine Migration zu Unity 2020.3 LTS und dem Mixed Reality OpenXR-Plug-In planen.