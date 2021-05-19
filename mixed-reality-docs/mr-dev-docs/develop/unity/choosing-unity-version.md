---
title: Auswählen einer Unity-Version und eines XR-Plug-Ins
description: Bleiben Sie über die neuesten Unity- und XR-Plug-In-Empfehlungen für die Entwicklung von HoloLens-Anwendungen auf dem laufenden.
author: hferrone
ms.author: v-hferrone
ms.date: 03/26/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Unity
ms.openlocfilehash: 3bdaa35f495d7a647a7cbf37ddcd4f85e96d74d0
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143675"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a>Auswählen einer Unity-Version und eines XR-Plug-Ins

Es wird derzeit empfohlen, **Unity 2019.4 LTS** zu installieren und ältere integrierte XR-Daten für die Mixed Reality-Entwicklung zu verwenden. Sie können aber auch Apps mit anderen Unity-Konfigurationen erstellen.

## <a name="unity-20194-lts-recommended"></a>Unity 2019.4 LTS (empfohlen)

Die derzeit von Microsoft empfohlene Unity-Konfiguration für HoloLens 2- und Windows Mixed Reality-Entwicklung ist **Unity 2019.4 LTS mit integrierter Legacy-XR-Unterstützung.**

Die beste Möglichkeit zum Installieren und Verwalten von Unity ist der <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity Hub]</a>. Wenn sie installiert ist, öffnen Sie Unity Hub:

1. Wählen Sie die **Registerkarte Installs (Installationen)** und dann **ADD (HINZUFÜGEN) aus.**
2. Wählen Sie Unity 2019.4 LTS aus, und klicken Sie auf **Weiter.**

![Neue Version des Unity-Hubs](images/unity-hub-img-01.png)

3. Überprüfen Sie die folgenden Komponenten unter **"Plattformen".**
    * **Buildunterstützung für Universelle Windows-Plattform** 
    * **Windows-Buildunterstützung (IL2CPP)**

![Unity: Option „Buildunterstützung für Universelle Windows-Plattform“](../images/Unity_Install_Option_UWP.png)

4. Wenn Sie Unity ohne diese Optionen installiert haben, können Sie diese über das Menü **"Module hinzufügen"** in Unity Hub hinzufügen:

![Unity: Option „Windows-Buildunterstützung“](../images/Unity_Install_Option_UWP2.png)

Klicken Sie hier, um mit der älteren integrierten XR in Unity 2019.4 LTS zu beginnen:

> [!div class="nextstepaction"]
> [Einrichten von legacy-integriertem XR](legacy-xr-support.md)

> [!NOTE]
> Unity hat die integrierte Legacy-XR-Unterstützung ab Unity 2019 als veraltet bezeichnet.  Unity 2019 bietet zwar ein neues XR-Plug-In-Framework, Microsoft empfiehlt diesen Pfad in Unity 2019 jedoch aufgrund von Azure Spatial Anchors-Inkompatibilitäten mit AR Foundation 2 nicht.  In Unity 2020 wird Azure Spatial Anchors im XR-Plug-In-Framework unterstützt.

Wenn Sie Apps für HoloLens (1. Generation) entwickeln, werden diese Headsets in Unity 2019 LTS mit integriertem Legacy-XR für den gesamten Lebenszyklus von Unity 2019 LTS bis Mitte 2022 weiterhin unterstützt.

## <a name="unity-20203-lts"></a>Unity 2020.3 LTS 

Wenn Sie **Unity 2020.3 LTS** verwenden, können Sie das **Windows XR-Plug-In** verwenden, um anwendungen HoloLens 2 Windows Mixed Reality entwickeln.

Es gibt jedoch bekannte Probleme, die sich auf die Hologrammstabilität und andere Features auf HoloLens 2 auswirken: 

* Holografische App-Remotinganwendungen, die das Universelle Windows-Plattform Buildziel verwenden, funktionieren nicht.
* Das Unity-Grafikaufträgesystem ist standardmäßig aktiviert, obwohl es nicht mit HoloLens-Projekten kompatibel ist.

Wenn Sie noch heute ein neues Projekt in Unity 2020 starten möchten, sollten Sie in den kommenden Monaten nach aktualisierten Unity-Builds und Windows XR-Plug-In-Builds suchen, bevor Sie Ihre App versenden.  Dadurch wird sichergestellt, dass Ihre Benutzer die richtige Hologrammstabilität erhalten.

> [!div class="nextstepaction"]
> [Verwenden des Windows XR-Plug-Ins](windows-xr-plugin.md)

### <a name="using-openxr"></a>Verwenden von OpenXR

Unity 2020.3 LTS unterstützt auch eine öffentliche Vorschauversion des Mixed Reality OpenXR-Plug-Ins. 

Das Mixed Reality OpenXR-Plug-In unterstützt AR Foundation 4.0 vollständig und stellt ARPlaneManager- und ARRaycastManager-Implementierungen bereit. Dadurch können Sie einmal Treffertestcode schreiben, der sich dann über HoloLens 2 und ARCore/ARKit-Smartphones und -Tablets erstreckt. 

Später in diesem Jahr wird **Unity 2020.3 LTS mit dem OpenXR-Plug-In** zur empfohlenen Unity-Konfiguration, und zukünftige HoloLens 2 Features in Unity werden nur über dieses Plug-In verfügbar gemacht.

> [!div class="nextstepaction"]
> [Verwenden des OpenXR-Plug-Ins](openxr-getting-started.md)

## <a name="unity-20211"></a>Unity 2021.1

Wenn Sie frühe **Unity 2021.1-Builds** ausprobieren, sollten Sie mit dem **OpenXR-Plug-In** fortschreiten, da das Windows XR-Plug-In dort veraltet ist.  Ab Unity 2021.2 ist das OpenXR-Plug-In der einzige Pfad für Mixed Reality Entwicklung, da das Windows XR-Plug-In nicht mehr unterstützt wird.

## <a name="unity-20184-lts"></a>Unity 2018.4 LTS

Wenn Sie bereits über ein Projekt mit Unity 2018.4 LTS verfügen, wird Ihre Unity-Engine nach der Veröffentlichung 2 Jahre lang unterstützt.  Unity 2018 LTS wird im Spring 2021 das Ende des Diensts erreichen.
