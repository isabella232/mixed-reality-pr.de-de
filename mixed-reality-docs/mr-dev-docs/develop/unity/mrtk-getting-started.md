---
title: Einführung in MRTK für Unity
description: Für neu einsteigende Entwickler, die sich für die Nutzung des MRTK interessieren
author: cre8ivepark
ms.author: dongpark
ms.date: 05/15/2019
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, Test, Mixed Reality Toolkit, MRTK-Version 2, MRTK, Tools, SDK, HoloLens, HoloLens 2, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, plattformübergreifend
ms.openlocfilehash: 6887d79d4a0737f3ed0f63af5686699fc7a1a2b6
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/17/2020
ms.locfileid: "97613444"
---
# <a name="introducing-mrtk-for-unity"></a>Einführung in MRTK für Unity

![MRTK](../../design/images/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a>Was ist das Mixed Reality Toolkit (MRTK)?
MRTK ist ein fantastisches Open-Source-Toolkit, das seit der ersten Veröffentlichung der HoloLens verfügbar ist. Das Toolkit wäre nicht so weit, wie es heute ist, ohne die harte Arbeit unserer mitwirkenden Entwicklercommunity. In Lauf der letzten drei Jahre haben wir auf das Feedback unserer Entwicklercommunity gehört und MRTK v2 aufgebaut, um den größten Bedenken Rechnung zu tragen.  

MRTK für Unity ist ein plattformübergreifendes Open Source-Entwicklungskit für Mixed Reality-Anwendungen. Das Toolkit bietet ein plattformübergreifendes Eingabesystem, Grundlagenkomponenten und gemeinsame Bausteine für räumliche Interaktionen. MRTK, Version 2, soll die Anwendungsentwicklung für Microsoft HoloLens, für immersive Windows Mixed Reality-Headsets (VR) und für die OpenVR-Plattform beschleunigen. Das Projekt ist darauf ausgerichtet, die Einstiegshürden zum Erstellen von Mixed Reality-Anwendungen zu verringern, und einen Beitrag für die Community auf diesem stetig wachsenden Gebiet zu leisten.

<br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCG]

Werfen Sie einen Blick in die [MRTK-Dokumentation auf GitHub](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html), und beginnen Sie mit der [Installationsanleitung](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html).


## <a name="new-with-mrtk-v2"></a>Neu in MRTK v2
Wir möchten unser andauerndes Engagement für diese Plattformtools betonen.  Tatsächlich haben wir das MRTK, Version 2, verwendet, um unsere Inbox-Erlebnisse zu entwickeln, wie etwa die vorgefertigte Setup-Erfahrung (OOBE) und unsere Mixed Reality-Tipps-Anwendung. Sie können außerdem damit rechnen, dass neue Funktionen von HoloLens 2 erstmalig über das MRTK verfügbar gemacht werden, da wir glauben, dies ist der richtige Weg für die Entwicklung unserer Plattform. 

### <a name="modular"></a>Modular
Wir haben das Toolkit modular aufgebaut, es ist also nicht notwendig, jeden Teil des Toolkits in Ihr Projekt zu integrieren.  Dies bietet in der Praxis eine Reihe von Vorteilen.  Es verringert die Größe Ihres Projekts und vereinfacht seine Verwaltung.  Da es aus skriptfähigen Objekten aufgebaut wurde und über eine Schnittstelle gesteuert wird, können Sie außerdem die enthaltenen Komponenten durch eigene ersetzen, um andere Dienste, Systeme und Plattformen zu unterstützen.

### <a name="cross-platform"></a>Plattformübergreifend
Andere Plattformen sind ein Thema, denn das Toolkit bietet plattformübergreifende Unterstützung.  Das bedeutet zwar nicht, dass jede einzelne Plattform unterstützt wird, wir haben aber sichergestellt, dass der Code des Toolkits auch dann funktioniert, wenn Sie ihr Buildziel auf eine andere Plattform umstellen.  Durch die Stabilität und Erweiterbarkeit des modularen Aufbaus gibt Ihren Apps die Möglichkeit, Unterstützung für mehrere Plattformen zu bieten, wie etwa ARCore, ARKit und OpenVR.

### <a name="performant"></a>Leistungsfähig
Für das Arbeiten mit mobilen Plattformen haben wir das Toolkit mit dem Augenmerk auf Leistung aufgebaut.  Das ist äußerst wichtig, und wir wollten sicherstellen, dass die Tools sich Ihnen nicht in den Weg stellen.

## <a name="see-also"></a>Siehe auch
* [Installieren der Tools](../install-the-tools.md)
* [MRTK – Installationshandbuch (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)
* [Startseite der MRTK-Dokumentation (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [Portieren von HoloToolkit/MRTK zu MRTK, Version 2 (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
