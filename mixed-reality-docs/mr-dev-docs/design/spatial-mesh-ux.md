---
title: Visualisierung räumlicher Netze
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: Gemischte Realität, hololens, UI-Steuerelemente, Interaktion, UI, UX, UX-Entwurf, räumliche Benutzeroberfläche, räumliche Interaktion, 3D-Benutzeroberfläche, 3D-UX
ms.openlocfilehash: 2c811edc14fbcc7c917fe9fa724f1cab23179a96
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2020
ms.locfileid: "91686091"
---
# <a name="spatial-mesh"></a>Raum-Mesh

![Raum-Mesh](images/MRTK_PulseShader_SpatialMesh.gif)

Durch die Visualisierung räumlicher Netze kann der Benutzer erfahren, wie ein Gerät die physische Umgebung erkennt und versteht. Zusätzlich zur Bereitstellung von räumlichem Kontext kann die richtige räumliche Gitter Visualisierung eine reizvolle und magische Darstellung schaffen.  

## <a name="design-guideline"></a>Entwurfsrichtlinie
Da es wichtig ist, dass der Benutzer auf Inhalte fokussiert und mit ihm interagiert, kann das fortlaufende und wiederholte visualisieren des räumlichen Netzes im Hintergrund ablenkend sein. Es wird empfohlen, die Umgebung sparsam zu visualisieren. Dies geschieht entweder nur einmal beim ersten Start oder wenn der Benutzer klar ist, dass das Umgebungs Netz durch Ziel-und Luftbild Speicher angezeigt werden soll. Dieses Verhalten kann in der hololens-Shell beobachtet werden.
<br>


## <a name="spatial-mesh-visualization-in-mrtk-mixed-reality-toolkit-for-unity"></a>Visualisierung räumlicher Netze in mrtk (Mixed Reality Toolkit) für Unity
Mrtk bietet mehrere Materialien für die Visualisierung räumlicher Netze.

- **MRTK_Wireframe. Matt, MRTK_Wireframe. Matt** : statisches Standard Mesh-Material, das die Gitter Kontur ohne Animation anzeigt. Dieses Material ist für Debuggingzwecke nützlich, da es die gesamten räumlichen Gitter Geometrien anzeigt. Dies wird jedoch nicht für die Produktion empfohlen.
<br>
<img src="images/SurfaceReconstruction.jpg" alt="Wireframe spatial mesh visualization" width="640px">

- **MRTK_SurfaceReconstruction. Matt** : dieses Material bietet einen animierten Pulse-Effekt auf das räumliche Mesh. Sie können dieses Material verwenden, um die Umgebung zu einem bestimmten Zeitpunkt ihrer Umgebung oder in der Eingabe des Benutzers zu visualisieren. Beispiele hierfür finden Sie in der **pulseshaderexamples. unity** -Szene.
<br>
<img src="images/MRTK_SRMesh_Pulse.jpg" alt="Pulse spatial mesh visualization" width="640px">
* Weitere Informationen finden Sie unter [mrtk-Spatial Awareness](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html) und [mrtk-Pulse Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/PulseShader/README.html) .

<br>

---

## <a name="see-also"></a>Weitere Informationen

* [Cursor](cursors.md)
* [Handstrahl](point-and-commit.md)
* [Schaltfläche](button.md)
* [Interaktionsfähiges Objekt](interactable-object.md)
* [Begrenzungsrahmen und App-Leiste](app-bar-and-bounding-box.md)
* [Manipulation](direct-manipulation.md)
* [Handmenü](hand-menu.md)
* [Nähemenü](near-menu.md)
* [Objektsammlung](object-collection.md)
* [Sprachbefehl](voice-input.md)
* [Tastatur](keyboard.md)
* [QuickInfo](tooltip.md)
* [Filmklappe](slate.md)
* [Schieberegler](slider.md)
* [Shader](shader.md)
* [Billboarding und Tag-along](billboarding-and-tag-along.md)
* [Anzeigen des Fortschritts](progress.md)
* [Oberflächenmagnetismus](surface-magnetism.md)
