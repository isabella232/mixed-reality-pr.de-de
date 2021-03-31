---
title: Auswählen einer Unity-Version und eines XR-Plug-ins
description: Bleiben Sie auf dem neuesten Stand mit den neuesten Empfehlungen für Unity und XR-Plug-Ins für die hololens-Anwendungsentwicklung.
author: hferrone
ms.author: v-hferrone
ms.date: 03/26/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-Unity, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Unity
ms.openlocfilehash: b8f5f0131da811393ee053541e0c2fa0c735472e
ms.sourcegitcommit: 6272d086a2856e8b514a719e1f9e3b78554be5be
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2021
ms.locfileid: "105938140"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a>Auswählen einer Unity-Version und eines XR-Plug-ins

Wir empfehlen zurzeit die **Installation von Unity 2019,4 LTS und die Verwendung von Legacy-integrierten XR** für die Entwicklung mit gemischter Realität. Außerdem können Sie Apps mit anderen Unity-Konfigurationen erstellen.

## <a name="unity-20194-lts-recommended"></a>Unity 2019,4 LTS (empfohlen)

Die zurzeit Empfohlene Unity-Konfiguration von Microsoft für hololens 2 und die Windows Mixed Reality-Entwicklung ist **Unity 2019,4 LTS mit der integrierten** Unterstützung von XR.

Die beste Möglichkeit zum Installieren und Verwalten von Unity besteht im <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity-Hub]</a>. Öffnen Sie nach der Installation den Unity-Hub:

1. Wählen Sie die Registerkarte **Installationen** und dann **Hinzufügen** aus.
2. Wählen Sie Unity 2019,4 LTS aus, und klicken Sie auf **weiter**

![Neue Version des Unity-Hubs 2010-32](images/unity-hub-img-01.png)

3. Überprüfen Sie die folgenden Komponenten unter **"Plattformen"**
    * **Universelle Windows-Plattform Build-Unterstützung** 
    * **Unterstützung für Windows-Builds (IL2CPP)**

![Unity-universelle Windows-Plattform Build-Unterstützungs Option](../images/Unity_Install_Option_UWP.png)

4. Wenn Sie Unity ohne diese Optionen installiert haben, können Sie Sie über das Menü **"Module hinzufügen"** im Unity-Hub hinzufügen:

![Unity-Windows-Buildunterstützung](../images/Unity_Install_Option_UWP2.png)

Klicken Sie hier, um mit der integrierten Version XR in Unity 2019,4 LTS zu beginnen:

> [!div class="nextstepaction"]
> [Einrichten von Legacy-integrierter XR](legacy-xr-support.md)

> [!NOTE]
> Unity hat seine ältere integrierte XR-Unterstützung seit Unity 2019 als veraltet markiert.  Während Unity 2019 ein neues XR-Plug-in-Framework bietet, wird dieser Pfad von Microsoft aufgrund von Inkompatibilitäten in Azure Spatial-verankert mit AR Foundation 2 derzeit nicht in Unity 2019 empfohlen.  In Unity 2020 wird Azure Spatial Anchor im XR-Plug-in-Framework unterstützt.

Wenn Sie Apps für hololens (1. Generation) entwickeln, werden diese Headsets in Unity 2019 LTS mit Legacy-integrierter XR für den vollständigen Lebenszyklus von Unity 2019 LTS bis Mitte 2022 unterstützt.

## <a name="unity-20203-lts"></a>Unity 2020,3 LTS 

Wenn Sie **Unity 2020,3 LTS** verwenden, können Sie das Windows- **XR-Plug** -in verwenden, um hololens 2-und Windows Mixed Reality-Anwendungen zu entwickeln.

Es gibt jedoch bekannte Probleme, die die – Hologramm-Stabilität und andere Features auf hololens 2 beeinflussen: 

* Die Tiefe Puffer Übermittlung wurde in aktuellen Unity 2020-Builds zurückgekehrt, was zu einer schwerwiegenden – Hologramm-Instabilität führt.
* Holographic App-Remoting-Anwendungen, die das universelle Windows-Plattform Build-Ziel verwenden, funktionieren nicht.
* Das Unity-Grafik Auftrags System ist standardmäßig eingeschaltet, obwohl es nicht mit hololens-Projekten kompatibel ist.

Wenn Sie noch heute ein neues Projekt in Unity 2020 starten möchten, sollten Sie sich in den kommenden Monaten für aktualisierte Unity-Builds und Windows-XR-Plug-in-Builds vor dem Versenden Ihrer APP informieren.  Dadurch wird sichergestellt, dass Ihre Benutzer über die richtige – Hologramm-Stabilität verfügen.

> [!div class="nextstepaction"]
> [Verwenden des Windows XR-Plug-ins](windows-xr-plugin.md)

### <a name="using-openxr"></a>Verwenden von openxr

Unity 2020,3 LTS unterstützt auch eine öffentliche Vorschau des **Mixed Reality openxr** -Plug-ins.

Das Mixed Reality openxr-Plug-in unterstützt AR Foundation 4,0 vollständig und stellt die Implementierungen arplanemanager und arraycastmanager bereit. Auf diese Weise können Sie Code für die Treffer Überprüfung schreiben, der dann die hololens 2-und Arcore-/Arkit-Telefone und-Tablets umfasst. 

Im weiteren Verlauf dieses Jahres wird **Unity 2020,3 LTS mit dem openxr-Plug-in** die empfohlene Unity-Konfiguration, und zukünftige hololens 2-Funktionen in Unity werden nur über dieses Plug-in verfügbar gemacht.  Sie können das Projekt jetzt hier starten. Wenn Ihr Projekt jedoch auf hololens 2 ausgerichtet ist, stoßen Sie derzeit auf die Stabilität von Unity 2020 – Hologramm und andere Probleme, die oben aufgeführt sind.  Stellen Sie sicher, dass Sie sich in den kommenden Monaten für aktualisierte Unity-Builds und openxr-Plug-in-Builds ansehen, bevor Sie Ihre APP versenden  Dadurch wird sichergestellt, dass Ihre Benutzer über die richtige – Hologramm-Stabilität verfügen. 

> [!div class="nextstepaction"]
> [Verwenden des openxr-Plug-ins](openxr-getting-started.md)

## <a name="unity-20211"></a>Unity 2021,1

Wenn Sie frühe **Unity 2021,1** -Builds ausprobieren, sollten Sie zum **openxr-Plug**-in wechseln, da das Windows-XR-Plug-in dort veraltet ist.  Ab Unity 2021,2 ist das openxr-Plug-in der einzige Pfad für die Entwicklung mit gemischter Realität, da das Windows-XR-Plug-in nicht mehr unterstützt wird.

## <a name="unity-20184-lts"></a>Unity 2018,4 LTS

Wenn Sie bereits über ein Projekt verfügen, das Unity 2018,4 LTS verwendet, wird Ihre Unity-Engine nach der Veröffentlichung weiterhin 2 Jahre lang unterstützt.  Unity 2018 LTS erreicht das Dienst Ende im Frühjahr 2021.
