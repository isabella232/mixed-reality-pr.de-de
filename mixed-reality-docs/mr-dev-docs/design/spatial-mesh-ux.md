---
title: Visualisierung räumlicher Gitternetze
description: Erfahren Sie mehr über Entwurfsrichtlinien und das Verständnis der physischen Umgebung mit der Visualisierung räumlicher Gitternetze im MRTK.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: Mixed Reality, HoloLens, UI-Steuerelemente, Interaktion, Ui, UX, UX-Design, räumliche Benutzeroberfläche, räumliche Interaktion, 3D-BENUTZEROBERFLÄCHE, 3D-Benutzeroberfläche, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 5bdcba60f38ac67bbf0f394337735f4a2d4ec423
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600629"
---
# <a name="spatial-mesh"></a>Raum-Mesh

![Raum-Mesh](images/MRTK_PulseShader_SpatialMesh.gif)

Benutzer erfahren, wie ein Gerät die physische Umgebung mithilfe der Visualisierung räumlicher Gitternetze wahrnimmt und versteht. Die richtige Visualisierung des räumlichen Gitternetzes kann eine ansprechende und magische Erfahrung schaffen und gleichzeitig räumlichen Kontext bereitstellen.  

## <a name="design-guideline"></a>Entwurfsrichtlinie

Es ist wichtig, dem Benutzer die Möglichkeit zu geben, sich auf Inhalte zu konzentrieren und mit ihnen zu interagieren. Die kontinuierliche Visualisierung des räumlichen Gitters im Hintergrund kann ablenkend sein. Es wird empfohlen, die Umgebung nur einmal beim ersten Start zu visualisieren, oder wenn der Benutzer deutlich anzeigt, dass er das Umgebungsgitternetz anzeigen möchte, indem er den Bereich anzielt und tippt. Sie können dieses Verhalten im Mixed Reality-Portal beobachten.
<br>

## <a name="spatial-mesh-visualization-in-mrtk-mixed-reality-toolkit-for-unity"></a>Visualisierung räumlicher Gitternetze im MRTK (Mixed Reality Toolkit) für Unity

MRTK stellt mehrere Materialien für die Visualisierung räumlicher Gitternetze bereit.

- **MRTK_Wireframe.mat, MRTK_Wireframe.mat:** Standardmäßiges statisches räumliches Gitternetzmaterial, das die Gitternetzgliederungen ohne Animation anzeigt. Dieses Material ist für Debugzwecke nützlich, da es die gesamten Geometrien des räumlichen Gitternetzes anzeigt. Es wird jedoch nicht für die Produktion empfohlen.
<br>
<img src="images/SurfaceReconstruction.jpg" alt="Wireframe spatial mesh visualization" width="640px">

- **MRTK_SurfaceReconstruction.mat:** Dieses Material gibt Ihnen einen animierten Pulse-Effekt auf das räumliche Netz. Sie können dieses Material verwenden, um die Umgebung zu einem bestimmten Zeitpunkt oder in der Eingabe des Benutzers zu visualisieren. Beispiele finden Sie unter **PulseShaderExamples.unity scene (PulseShaderExamples.unity-Szene).**
<br>
<img src="images/MRTK_SRMesh_Pulse.jpg" alt="Pulse spatial mesh visualization" width="640px">

* Weitere Informationen finden Sie unter [MRTK – Räumliche Wahrnehmung](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started) und [MRTK – Pulse Shader](/windows/mixed-reality/mrtk-unity/features/experimental/pulse-shader).

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