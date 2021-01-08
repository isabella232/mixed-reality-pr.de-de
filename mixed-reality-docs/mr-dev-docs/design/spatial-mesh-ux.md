---
title: Visualisierung räumlicher Netze
description: Erfahren Sie mehr über Entwurfs Richtlinien und Kenntnisse der physischen Umgebung mit räumlicher Gitter Visualisierung in mrtk.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: Gemischte Realität, hololens, UI-Steuerelemente, Interaktion, UI, UX, UX-Entwurf, räumliche Benutzeroberfläche, räumliche Interaktion, 3D-Benutzeroberfläche, 3D-UX, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, hololens, mrtk, Mixed Reality Toolkit
ms.openlocfilehash: 0f9cdc218c6fe54b8892c39a6a76f023e203d334
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009920"
---
# <a name="spatial-mesh"></a>Raum-Mesh

![Raum-Mesh](images/MRTK_PulseShader_SpatialMesh.gif)

Benutzer erfahren, wie ein Gerät die physische Umgebung durch eine räumliche Mesh-Visualisierung wahrnimmt und versteht. Die richtige räumliche Gitter Visualisierung kann bei der Bereitstellung räumlichen Kontexts eine reizvolle und magische Darstellung schaffen.  

## <a name="design-guideline"></a>Entwurfsrichtlinie

Es ist wichtig, dass der Benutzer den Fokus auf Inhalte hat und mit ihm interagiert. Die fortlaufende Visualisierung des räumlichen Netzes im Hintergrund kann ablenkend sein. Es wird empfohlen, die Umgebung sparsam zu visualisieren, entweder nur einmal beim ersten Start oder wenn der Benutzer deutlich anzeigt, dass er das Umgebungs Netz durch Ziel und Luft tippen anzeigen soll. Dieses Verhalten können Sie im Mixed Reality-Portal beobachten.
<br>

## <a name="spatial-mesh-visualization-in-mrtk-mixed-reality-toolkit-for-unity"></a>Visualisierung räumlicher Netze in mrtk (Mixed Reality Toolkit) für Unity

Mrtk bietet mehrere Materialien für die Visualisierung räumlicher Netze.

- **MRTK_Wireframe. Matt, MRTK_Wireframe. Matt**: statisches Standard Mesh-Material, das die Gitter Kontur ohne Animation anzeigt. Dieses Material ist für Debuggingzwecke nützlich, da es die gesamten räumlichen Gitter Geometrien anzeigt. Dies wird jedoch nicht für die Produktion empfohlen.
<br>
<img src="images/SurfaceReconstruction.jpg" alt="Wireframe spatial mesh visualization" width="640px">

- **MRTK_SurfaceReconstruction. Matt**: dieses Material bietet einen animierten Pulse-Effekt auf das räumliche Mesh. Sie können dieses Material verwenden, um die Umgebung zu einem bestimmten Zeitpunkt oder in der Eingabe des Benutzers in der Luft Eingabe anzuzeigen. Beispiele hierfür finden Sie in der **pulseshaderexamples. unity** -Szene.
<br>
<img src="images/MRTK_SRMesh_Pulse.jpg" alt="Pulse spatial mesh visualization" width="640px">
* Weitere Informationen finden Sie unter [mrtk-Spatial Awareness](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html) und [mrtk-Pulse Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/PulseShader/README.html).

<br>

---

## <a name="see-also"></a>Siehe auch

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
