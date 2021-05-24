---
title: Auswählen einer Unity-Version und eines XR-Plug-Ins
description: Bleiben Sie über die neuesten Unity- und XR-Plug-In-Empfehlungen für die HoloLens-Anwendungsentwicklung auf dem Laufenden.
author: hferrone
ms.author: v-hferrone
ms.date: 03/26/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Unity
ms.openlocfilehash: febeb46972935a02d9c945e2a0cafabebedd0715
ms.sourcegitcommit: b195b82f7e83e2ac4f5d8937d169e9dcb865d46d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2021
ms.locfileid: "110333382"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a>Auswählen einer Unity-Version und eines XR-Plug-Ins

Wir empfehlen derzeit die **Installation von Unity 2019.4 LTS und die Verwendung von Legacy-integriertem XR** für Mixed Reality Entwicklung. Sie können aber auch Apps mit anderen Unity-Konfigurationen erstellen.

## <a name="unity-20194-lts-recommended"></a>Unity 2019.4 LTS (empfohlen)

Die aktuelle empfohlene Unity-Konfiguration von Microsoft für HoloLens 2 und Windows Mixed Reality Entwicklung ist **Unity 2019.4 LTS mit legacy-integrierter XR-Unterstützung.**

Die beste Möglichkeit zum Installieren und Verwalten von Unity ist <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity Hub]</a>. Öffnen Sie nach der Installation Unity Hub:

1. Wählen Sie die Registerkarte **Installationen** und dann **HINZUFÜGEN** aus.
2. Wählen Sie Unity 2019.4 LTS aus, und klicken Sie auf **Weiter.**

![Unity-Hub in der neuen Version](images/unity-hub-img-01.png)

3. Überprüfen Sie die folgenden Komponenten unter **"Plattformen".**
    * **Buildunterstützung für Universelle Windows-Plattform** 
    * **Windows-Buildunterstützung (IL2CPP)**

![Unity: Option „Buildunterstützung für Universelle Windows-Plattform“](../images/Unity_Install_Option_UWP.png)

4. Wenn Sie Unity ohne diese Optionen installiert haben, können Sie sie über das Menü **"Module hinzufügen"** in Unity Hub hinzufügen:

![Unity: Option „Windows-Buildunterstützung“](../images/Unity_Install_Option_UWP2.png)

Klicken Sie hier, um mit legacy-integriertem XR in Unity 2019.4 LTS zu beginnen:

> [!div class="nextstepaction"]
> [Einrichten von Legacy-integriertem XR](legacy-xr-support.md)

> [!NOTE]
> Unity hat die legacy-integrierte XR-Unterstützung ab Unity 2019 als veraltet erklärt.  Während Unity 2019 ein neues XR-Plug-In-Framework bietet, empfiehlt Microsoft diesen Pfad in Unity 2019 aufgrund von Azure Spatial Anchors Inkompatibilitäten mit AR Foundation 2 derzeit nicht.  In Unity 2020 wird Azure Spatial Anchors im XR-Plug-In-Framework unterstützt.

Wenn Sie Apps für HoloLens (1. Generation) entwickeln, werden diese Headsets in Unity 2019 LTS mit legacy-integriertem XR für den gesamten Lebenszyklus von Unity 2019 LTS bis Mitte 2022 weiterhin unterstützt.

## <a name="unity-20203-lts"></a>Unity 2020.3 LTS 

Wenn Sie **Unity 2020.3 LTS** verwenden, können Sie das **Windows XR-Plug-In** verwenden, um HoloLens 2 und Windows Mixed Reality Anwendungen zu entwickeln.

Es gibt jedoch bekannte Probleme, die sich auf die Hologrammstabilität und andere Features HoloLens 2: 

* Holographic App-Remotinganwendungen, die Universelle Windows-Plattform Buildziel verwenden, funktionieren nicht.
* Das Unity-Grafikaufträgesystem ist standardmäßig aktiviert, obwohl es nicht mit HoloLens-Projekten kompatibel ist.

Wenn Sie Unity 2020 verwenden möchten, müssen Sie ein Upgrade auf Unity 2020.3.6f1 oder höher durchführen, um die ordnungsgemäße Hologrammstabilität für Ihre Benutzer sicherzustellen.

> [!div class="nextstepaction"]
> [Verwenden des Windows XR-Plug-Ins](windows-xr-plugin.md)

### <a name="using-openxr"></a>Verwenden von OpenXR

Unity 2020.3 LTS unterstützt auch eine öffentliche Vorschau des Mixed Reality **OpenXR-Plug-Ins.**

Das Mixed Reality OpenXR-Plug-In unterstützt AR Foundation 4.0 vollständig und stellt ARPlaneManager- und ARRaycastManager-Implementierungen zur Verfügung. Auf diese Weise können Sie Treffertestcode schreiben, der sich dann über HoloLens 2 und ARCore/ARKit-Smartphones und -Tablets erstreckt. 

Später in diesem Jahr wird **Unity 2020.3 LTS** mit dem OpenXR-Plug-In zur empfohlenen Unity-Konfiguration, und zukünftige HoloLens 2-Features in Unity werden nur über dieses Plug-In verfügbar gemacht.

> [!div class="nextstepaction"]
> [Verwenden des OpenXR-Plug-Ins](openxr-getting-started.md)

## <a name="unity-20211"></a>Unity 2021.1

Wenn Sie frühe **Unity 2021.1-Builds** ausprobieren, sollten Sie mit dem **OpenXR-Plug-In** vorankommen, da das Windows XR-Plug-In dort veraltet ist.  Ab Unity 2021.2 ist das OpenXR-Plug-In der einzige Pfad für die Mixed Reality-Entwicklung, da das Windows XR-Plug-In nicht mehr unterstützt wird.

## <a name="unity-20184-lts"></a>Unity 2018.4 LTS

Wenn Sie bereits über ein Projekt mit Unity 2018.4 LTS verfügen, wird Ihre Unity-Engine nach der Veröffentlichung zwei Jahre lang weiterhin unterstützt.  Unity 2018 LTS erreicht das Ende des Diensts im Januar 2021.
