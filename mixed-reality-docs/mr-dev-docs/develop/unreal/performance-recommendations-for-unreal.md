---
title: Leistungsempfehlungen für Unreal
description: Empfehlungen für optimale Leistung von Mixed Reality-Apps in Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Leistung, Optimierung, Einstellungen, Dokumentation
ms.openlocfilehash: 295f5c3653d02e9ab7ab4cd51dba57cafb5b291f
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609621"
---
# <a name="performance-recommendations-for-unreal"></a>Leistungsempfehlungen für Unreal

Die Unreal Engine besitzt zahlreiche Funktionen, die die Leistung einer App steigern können, die alle auf der unter [Leistungsempfehlungen für Mixed Reality](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) dargelegten Diskussion basieren. Sie sollten sich zunächst über Engpässe bei Anwendungen, Analyse und Profilerstellung für Mixed Reality-Apps und allgemeine Leistungsfixes informieren, bevor Sie weiterlesen.

## <a name="recommended-unreal-project-settings"></a>Empfohlenen Unreal-Projekteinstellungen
Sie finden jede der folgenden Einstellungen unter **Edit > Project Settings** (Bearbeiten > Projekteinstellungen).

1. Mit dem mobilen VR-Renderer:
    * Scrollen Sie zum Abschnitt **Project**, wählen Sie **Target Hardware** (Zielhardware) aus, und legen Sie die Zielplattform auf **Mobile/Tablet** fest.

![Zieleinstellung „Mobile“](images/unreal/performance-recommendations-img-01.png)

2. Verwenden des Forward Renderers: 
    * Der Forward Renderer eignet sich aufgrund der Anzahl von Funktionen, die einzeln deaktiviert werden können, wesentlich besser für Mixed Reality als die standardmäßige verzögerte Renderingpipeline. 
    * Weitere Informationen finden Sie in der [Dokumentation zu Unreal](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html).

![Vorwärtsrendering](images/unreal/performance-recommendations-img-04.png)

3. In der mobilen Multiansicht:
    * Scrollen Sie zum Abschnitt **Engine**, wählen Sie **Rendering** aus, erweitern Sie den Abschnitt **VR**, und aktivieren Sie sowohl **Instanced Stereo** (Instanziiertes Stereo) als auch **Mobile Multi-View** (Mobile Multiansicht). Mobile-HDR sollte deaktiviert werden.

![VR-Renderingeinstellungen](images/unreal/performance-recommendations-img-03.png)

4. Stellen Sie sicher, dass **Standard** oder **D3D12** als **Standard-RHI**, ausgewählt ist, wenn OpenXR verwendet wird.
    * Wenn Sie **D3D11** auswählen, wirkt sich dies negativ auf die Leistung aus, da die Plattform einen zusätzlichen Renderdurchlauf ausführt. **D3D12** sollte zusätzlich zur Vermeidung des zusätzlichen Renderdurchlaufs Leistungsverbesserungen beim Rendering bewirken.

![Standard-RHI](images/unreal/performance-recommendations-img-09.png)

5. Deaktivieren von Vertex Fogging: 
    * Vertex-Fogging wendet an jedem Scheitelpunkt in einem Polygon Nebelberechnungen an und interpoliert die Ergebnisse dann auf der Vorderseite des Polygons. Wenn Ihr Spiel keinen Nebel verwendet, empfehlen wir, Vertex Fogging zu deaktivieren, um die Schattierungsleistung zu erhöhen.

![Vertex-Fogging-Optionen](images/unreal/performance-recommendations-img-05.png)

6. Deaktivieren des Okklusionscullings:
    * Scrollen Sie zum Abschnitt **Engine**, wählen Sie **Rendering** aus, erweitern Sie den Bereich **Culling**, und deaktivieren Sie **Occlusion Culling**.
        + Wenn Sie das Okklusionsculling für das Rendern einer detailreichen Szene benötigen, empfiehlt es sich, unter **Engine > Rendering** die Option **Support Software Occlusion Culling** (Softwareokklusionsculling unterstützen) zu aktivieren. Die Arbeit lässt Unreal von der CPU erledigen und vermeidet GPU-Okklusionsabfragen, deren Leistung auf HoloLens 2 schlecht ist.
    * Okklusionsculling in der GPU auf mobilen Geräten ist langsam. Im Allgemeinen ist es sinnvoll, dass die GPU sich hauptsächlich um das Rendering kümmert. Wenn Sie vermuten, dass Okklusion die Leistung verbessert, versuchen Sie stattdessen, Softwareokklusion zu aktivieren. 

> [!NOTE]
> Das Aktivieren von Softwareokklusion kann die Leistung auch verschlechtern, wenn die CPU durch eine hohe Anzahl von Zeichenaufrufen bereits stark ausgelastet ist.

![Deaktivieren des Okklusionscullings](images/unreal/performance-recommendations-img-02.png)

7. Durchlauf zum Deaktivieren der benutzerdefinierten Tiefenschablone:
    * Für das Deaktivieren der benutzerdefinierten Tiefenschablone ist ein zusätzlicher Durchgang erforderlich, was bedeutet, dass es langsam ist. Transparenz ist bei Unreal ebenfalls langsam. Weitere Informationen finden Sie in der [Dokumentation zu Unreal](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html).

![Tiefenschablone](images/unreal/performance-recommendations-img-06.png)

8. Verringern von überlappenden Schattenkarten: 
    * Durch das Verringern der Anzahl der Schattenkarten wird die Leistung verbessert. Im Allgemeinen sollten Sie die Eigenschaft auf 1 festlegen, es sei denn, es gibt einen sichtbaren Qualitätsverlust. 

![Überlappende Schattenkarten](images/unreal/performance-recommendations-img-07.png)

## <a name="optional-settings"></a>Optionale Einstellungen

> [!NOTE]
> Mit den folgenden Einstellungen kann möglicherweise die Leistung verbessert werden, aber um den Preis, dass bestimmte Features deaktiviert werden. Verwenden Sie diese Einstellungen nur, wenn Sie sicher sind, dass Sie die betreffenden Features nicht benötigen.

1. Verringerung der Shaderpermutation bei mobilen Geräten
    * Wenn sich Ihre Lichter nicht unabhängig von der Kamera bewegen, können Sie den Eigenschaftswert unbedenklich auf 0 festlegen. Der Hauptvorteil besteht darin, dass es dies Unreal ermöglicht, mehrere Shaderpermutationen auszusortieren, sodass die Shaderkompilierung beschleunigt wird.

![Verringerung der Shaderpermutation bei mobilen Geräten](images/unreal/performance-recommendations-img-08.png)

## <a name="see-also"></a>Siehe auch
* [Leistungsrichtlinien für die Unreal-Engine auf mobilen Geräten]( https://docs.unrealengine.com/Platforms/Mobile/Performance/index.html)