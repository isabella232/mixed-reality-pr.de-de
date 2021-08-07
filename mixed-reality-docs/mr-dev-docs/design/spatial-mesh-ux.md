---
title: Visualisierung räumlicher Gitternetze
description: Erfahren Sie mehr über Entwurfsrichtlinien und das Verständnis der physischen Umgebung mit räumlicher Gitternetzvisualisierung in MRTK.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: Mixed Reality, HoloLens, UI-Steuerelemente, Interaktion, Ui, ux, UX Design, räumliche Benutzeroberfläche, räumliche Interaktion, 3D-Benutzeroberfläche, 3D-Benutzeroberfläche, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 7fcba586f55e6131235d031327da131aa8ba6c97958e4ac282a8f8d048d37992
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115216284"
---
# <a name="spatial-mesh"></a>Raum-Mesh

![Raum-Mesh](images/MRTK_PulseShader_SpatialMesh.gif)

Benutzer erfahren, wie ein Gerät die physische Umgebung durch räumliche Gitternetzvisualisierung wahrnimmt und versteht. Eine ordnungsgemäße Visualisierung des räumlichen Gitters kann ein Darstellungs- und Erlebniserlebnis schaffen und gleichzeitig räumlichen Kontext bereitstellen.  

## <a name="design-guideline"></a>Entwurfsrichtlinie

Es ist wichtig, dem Benutzer zu erlauben, sich auf Inhalte zu konzentrieren und mit ihnen zu interagieren. Die kontinuierliche Visualisierung des räumlichen Gitters im Hintergrund kann störend sein. Es wird empfohlen, die Umgebung nur einmal beim ersten Start zu visualisieren, oder wenn der Benutzer deutlich zeigt, dass er das Umgebungsgitternetz durch Ausrichtung und Tippen auf die Luft anzeigen möchte. Sie können dieses Verhalten in der Mixed Reality-Portal.
<br>

## <a name="spatial-mesh-visualization-in-mrtk-mixed-reality-toolkit-for-unity"></a>Visualisierung räumlicher Gitternetze im MRTK (Mixed Reality Toolkit) für Unity

MRTK stellt mehrere Materialien für die Visualisierung räumlicher Gitternetze zur Verfügung.

- **MRTK_Wireframe.mat, MRTK_Wireframe.mat:** Statisches standardbezogenes Gitternetzmaterial, das die Gitternetzgliederungen ohne Animation zeigt. Dieses Material ist für Dasbuggen nützlich, da es die gesamten Geometrien des räumlichen Gitters zeigt. Dies wird jedoch nicht für die Produktion empfohlen.
<br>
<img src="images/SurfaceReconstruction.jpg" alt="Wireframe spatial mesh visualization" width="640px">

- **MRTK_SurfaceReconstruction.mat:** Dieses Material gibt Ihnen einen animierten Pulse-Effekt auf das räumliche Netz. Sie können dieses Material verwenden, um die Umgebung zu einem bestimmten Zeitpunkt oder in der Eingabe des Benutzers in die Luft zu visualisieren. Die Beispiele finden Sie unter **PulseShaderExamples.unity-Szene.**
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