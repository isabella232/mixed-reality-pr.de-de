---
title: Einführung in MRTK für Unity
description: Machen Sie Ihre ersten Schritte mit allem, was das plattformübergreifende Mixed Reality-Toolkit für neue Mixed Reality-Entwickler bereithält.
author: cre8ivepark
ms.author: dongpark
ms.date: 05/15/2019
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, Test, Mixed Reality Toolkit, MRTK-Version 2, MRTK, Tools, SDK, HoloLens, HoloLens 2, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, plattformübergreifend
ms.openlocfilehash: 6d9e43a3e5ef59226dc6396de46d1295181c07f950ab9255eaf8503f973a2f43
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187645"
---
# <a name="introducing-mrtk-for-unity"></a>Einführung in MRTK für Unity

![MRTK](../../design/images/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a>Was ist das Mixed Reality Toolkit (MRTK)?

MRTK ist ein fantastisches Open-Source-Toolkit, das seit der ersten Veröffentlichung der HoloLens verfügbar ist. Das Toolkit wäre nicht so weit, wie es heute ist, ohne die harte Arbeit unserer mitwirkenden Entwicklercommunity. In Lauf der letzten drei Jahre haben wir auf das Feedback unserer Entwicklercommunity gehört und MRTK v2 aufgebaut, um den größten Bedenken Rechnung zu tragen.  

MRTK für Unity ist ein plattformübergreifendes Open Source-Entwicklungskit für Mixed Reality-Anwendungen. Die einfachste Möglichkeit zum Installieren des Toolkits ist unsere neue Mixed Reality-Featuretoolanwendung. Befolgen Sie unsere [installations- und Verwendungsanweisungen](welcome-to-mr-feature-tool.md), und wählen Sie in der Kategorie „Mixed Reality-Toolkit“ das Paket **Mixed Reality Toolkit Foundation** aus.

MRTK für Unity bietet ein plattformübergreifendes Eingabesystem, Grundlagenkomponenten und gemeinsame Bausteine für räumliche Interaktionen. MRTK, Version 2, soll die Anwendungsentwicklung für Microsoft HoloLens, für immersive Windows Mixed Reality-Headsets (VR) und für die OpenVR-Plattform beschleunigen. Das Projekt ist darauf ausgerichtet, die Einstiegshürden zum Erstellen von Mixed Reality-Anwendungen zu verringern, und einen Beitrag für die Community auf diesem stetig wachsenden Gebiet zu leisten.

<br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCG]

> [!div class="nextstepaction"]
> [Probieren Sie unsere MRTK-Tutorials aus](tutorials/mr-learning-base-01.md)

Weitere Details zu Features finden Sie in der [MRTK-Dokumentation](/windows/mixed-reality/mrtk-unity).

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
* [Mixed Reality-Featuretool](welcome-to-mr-feature-tool.md)
* [Entwickeln mit MRTK für Unity](unity-development-overview.md)
* [Startseite der MRTK-Dokumentation](/windows/mixed-reality/mrtk-unity/)
* [Portieren von HoloToolkit/MRTK zu MRTK, Version 2](/windows/mixed-reality/mrtk-unity/updates-deployment/htk-to-mrtk-porting-guide)
