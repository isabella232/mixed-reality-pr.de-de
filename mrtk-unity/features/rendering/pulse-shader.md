---
title: Impuls-Shader
description: Beschreibung für Pulse-Shader in MRTK.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 0b26242d71bbe080e440f9c52a009e29000ab00b
ms.sourcegitcommit: 114c304a416bfe9d9b294c4adbb4c23cbe60ea4e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2021
ms.locfileid: "114224208"
---
# <a name="pulse-shader"></a>Impuls-Shader

![MRTK_SpatialMesh_Pulse](https://user-images.githubusercontent.com/13754172/68261851-3489e200-fff6-11e9-9f6c-5574a7dd8db7.gif)

Verwenden Sie den Pulse-Shader, um einen visuellen Pulse-Effekt über Oberflächenergütung, artikuliertes Handgitter oder andere Gitternetze zu animieren.

## <a name="shader-and-material"></a>Shader und Material

Die folgenden Materialien verwenden **SR_Triangles** Shader. Sie können verschiedene Optionen konfigurieren, z. B. Füllfarbe, Linienfarbe und Pulsfarbe.

- **MRTK_Pulse_SpatialMeshBlue.mat** 
- **MRTK_Pulse_SpatialMeshPurple.mat** 
- **MRTK_Pulse_ArticulatedHandMeshBlue.mat** 
- **MRTK_Pulse_ArticulatedHandMeshPurple.mat** 

## <a name="prerequisites"></a>Voraussetzungen

Stellen Sie für das Beispiel für räumliches Netz sicher, dass MRTK_Pulse_SpatialMeshBlue.mat oder MRTK_Pulse_SpatialMeshPurple.mat unter MixedRealityToolkit-Objekt -> Spatial Awareness Profile -> Display Einstellungen -> Visible Material zugewiesen ist.

Stellen Sie für das Handgitterbeispiel sicher, dass MRTK_Pulse_ArticulatedHandMeshBlue.mat oder MRTK_Pulse_ArticulatedHandMeshPurple.mat in ArticulatedHandMesh.prefab zugewiesen ist, das selbst in MRTK Einstellungen -> Input -> Hand Tracking -> Hand Mesh Prefab zugewiesen werden sollte.

## <a name="how-it-works"></a>Funktionsweise

Der Handgitter-Shader verwendet UVs, um den Puls entlang des Handgitters zu ordnen und die Hand zu ausblenden. Der Oberflächenrekonstruktions-Shader verwendet die Scheitelpunktpositionen, um den Puls zu zuordnen.

## <a name="spatial-mesh-example---pulseshaderspatialmeshexampleunity"></a>Spatial Mesh-Beispiel: PulseShaderSpatialMeshExample.unity

Ähnlich wie HoloLens 2 Shell-Erfahrung können Sie mit dem Handstrahl in die Luft tippen und zeigen, um einen pulsenden Effekt auf das räumliche Netz zu erzeugen. Die Beispielszene enthält das ExampleSpatialMesh-Objekt, bei dem es sich um ein Testobjekt für räumliche Gittermodelldaten für den Unity-Spielmodus handelt. Dieses Objekt wird deaktiviert und auf dem Gerät ausgeblendet.

**Das Skript PulseShaderSpatialMeshHandler.cs** generiert den Pulse-Effekt auf das räumliche Netz an der Trefferpunktposition, wenn `PulseOnSelect` true ist. Die -Eigenschaft kann auch im Material selbst für eine sich wiederholende Animation auf  `Auto Pulse` TRUE festgelegt werden.  In der Beispielszene wird dieses Skript an das PulseShaderSpatialMeshParent-Prefab angefügt.  Auf dieses Prefab wird unter der Spatial Awareness Profile through Runtime Spatial Mesh Prefab-Eigenschaft verwiesen. Zur Laufzeit wird das PulseShaderSpatialMeshParent-Prefab instanziiert und der Hierarchie räumlicher Gitternetze hinzugefügt (dieses Verhalten kann nur auf dem Gerät im Editor nicht beobachtet werden).

## <a name="hand-mesh-example---pulseshaderhandmeshexampleunity"></a>Hand Mesh-Beispiel: PulseShaderHandMeshExample.unity

Diese Beispielszene veranschaulicht die Handgittervisualisierung mithilfe eines Pulse Shaders. Wenn eine Hand vom Gerät erkannt HoloLens gerät, wird die Pulse-Animation einmal ausgelöst. Dieses visuelle Feedback kann die Interaktionsvertrauen des Benutzers erhöhen. 

**Das Skript PulseShaderHandMeshHandler.cs** generiert pulse effect auf das zugewiesene Material. Standardmäßig ist "Pulse On Hand Detected" aktiviert.
