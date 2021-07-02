---
title: Pulse-Shader
description: Beschreibung zu Pulse-Shadern im MRTK.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 087806d48c7304d43f8383285cbaa2a12d8bf99a
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176308"
---
# <a name="pulse-shader"></a>Pulse-Shader

![MRTK_SpatialMesh_Pulse](https://user-images.githubusercontent.com/13754172/68261851-3489e200-fff6-11e9-9f6c-5574a7dd8db7.gif)

Verwenden Sie den Pulse-Shader, um einen visuellen Pulse-Effekt über die Oberflächenrekonstruktion, das artikulierte Handgitternetz oder andere Gitter zu animieren.

## <a name="shader-and-material"></a>Shader und Material

In den folgenden Materialien **wird SR_Triangles** Shader verwendet. Sie können verschiedene Optionen konfigurieren, z. B. Füllfarbe, Linienfarbe und Pulsefarbe.

- **MRTK_Pulse_SpatialMeshBlue.mat** 
- **MRTK_Pulse_SpatialMeshPurple.mat** 
- **MRTK_Pulse_ArticulatedHandMeshBlue.mat** 
- **MRTK_Pulse_ArticulatedHandMeshPurple.mat** 

## <a name="prerequisites"></a>Voraussetzungen

Stellen Sie für das Beispiel für ein räumliches Gitternetz sicher, dass MRTK_Pulse_ArticulatedHandMeshBlue.mat oder MRTK_Pulse_ArticulatedHandMeshPurple.mat unter MRTK Einstellungen -> Spatial Awareness -> Display Einstellungen -> Visible Material zugewiesen ist.

Stellen Sie für das Handgitternetzbeispiel sicher, dass MRTK_Pulse_SpatialMeshBlue.mat oder MRTK_Pulse_SpatialMeshPurple.mat in "ArticulatedHandMesh.prefab" zugewiesen ist, das selbst in MRTK Einstellungen -> Input -> Hand Tracking -> Hand Mesh Prefab zugewiesen werden sollte.

## <a name="how-it-works"></a>Funktionsweise

Der Handnetz-Shader verwendet UVs, um den Pulse entlang des Handgitternetzes zuzuordnen und das Handgehüt auszublenden. Der Shader für die Oberflächenrekonstruktion verwendet die Scheitelpunktpositionen, um den Pulse zuzuordnen.

## <a name="spatial-mesh-example---pulseshaderspatialmeshexampleunity"></a>Spatial Mesh-Beispiel : PulseShaderSpatialMeshExample.unity

Ähnlich wie bei HoloLens 2 Shell können Sie mit dem Handstrahl zeigen und in die Luft tippen, um einen pulsierenden Effekt auf das räumliche Netz zu generieren. Die Beispielszene enthält das ExampleSpatialMesh-Objekt, bei dem es sich um räumliche Testgittermodelldaten für den Spielmodus von Unity handelt. Dieses Objekt wird deaktiviert und auf dem Gerät ausgeblendet.

Das Skript **PulseShaderSpatialMeshHandler.cs** generiert den Pulse-Effekt auf das räumliche Gitternetz an der Trefferpunktposition, wenn `PulseOnSelect` true ist. Die  `Auto Pulse` -Eigenschaft kann auch im Material selbst für eine sich wiederholende Animation auf TRUE festgelegt werden.  In der Beispielszene ist dieses Skript an das Prefab PulseShaderSpatialMeshParent angefügt.  Auf dieses Prefab wird unter der Spatial Awareness Profile through Runtime Spatial Mesh Prefab-Eigenschaft verwiesen. Während der Laufzeit wird das PulseShaderSpatialMeshParent-Prefab instanziiert und der Hierarchie des räumlichen Gitternetzes hinzugefügt (nur auf dem Gerät kann dieses Verhalten im Editor nicht beobachtet werden).

## <a name="hand-mesh-example---pulseshaderhandmeshexampleunity"></a>Hand Mesh-Beispiel – PulseShaderHandMeshExample.unity

In dieser Beispielszene wird die Visualisierung des Handgitternetzes mithilfe des Pulse-Shaders veranschaulicht. Wenn eine Hand vom HoloLens Gerät erkannt wird, wird die Pulse-Animation einmal ausgelöst. Dieses visuelle Feedback kann die Interaktionssicherheit des Benutzers erhöhen. 

Das Skript **PulseShaderHandMeshHandler.cs** generiert Einen Pulse-Effekt auf das zugewiesene Material. Standardmäßig ist "Pulse On Hand Detected" aktiviert.
