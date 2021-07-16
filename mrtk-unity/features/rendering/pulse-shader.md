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
# <a name="pulse-shader"></a><span data-ttu-id="91a01-104">Impuls-Shader</span><span class="sxs-lookup"><span data-stu-id="91a01-104">Pulse shader</span></span>

![MRTK_SpatialMesh_Pulse](https://user-images.githubusercontent.com/13754172/68261851-3489e200-fff6-11e9-9f6c-5574a7dd8db7.gif)

<span data-ttu-id="91a01-106">Verwenden Sie den Pulse-Shader, um einen visuellen Pulse-Effekt über Oberflächenergütung, artikuliertes Handgitter oder andere Gitternetze zu animieren.</span><span class="sxs-lookup"><span data-stu-id="91a01-106">Use the pulse shader to animate a visual pulse effect over surface reconstruction, articulated hand mesh, or any other meshes.</span></span>

## <a name="shader-and-material"></a><span data-ttu-id="91a01-107">Shader und Material</span><span class="sxs-lookup"><span data-stu-id="91a01-107">Shader and material</span></span>

<span data-ttu-id="91a01-108">Die folgenden Materialien verwenden **SR_Triangles** Shader.</span><span class="sxs-lookup"><span data-stu-id="91a01-108">Following materials use **SR_Triangles** shader.</span></span> <span data-ttu-id="91a01-109">Sie können verschiedene Optionen konfigurieren, z. B. Füllfarbe, Linienfarbe und Pulsfarbe.</span><span class="sxs-lookup"><span data-stu-id="91a01-109">You can configure various options such as fill color, line color, and pulse color.</span></span>

- <span data-ttu-id="91a01-110">**MRTK_Pulse_SpatialMeshBlue.mat**</span><span class="sxs-lookup"><span data-stu-id="91a01-110">**MRTK_Pulse_SpatialMeshBlue.mat**</span></span> 
- <span data-ttu-id="91a01-111">**MRTK_Pulse_SpatialMeshPurple.mat**</span><span class="sxs-lookup"><span data-stu-id="91a01-111">**MRTK_Pulse_SpatialMeshPurple.mat**</span></span> 
- <span data-ttu-id="91a01-112">**MRTK_Pulse_ArticulatedHandMeshBlue.mat**</span><span class="sxs-lookup"><span data-stu-id="91a01-112">**MRTK_Pulse_ArticulatedHandMeshBlue.mat**</span></span> 
- <span data-ttu-id="91a01-113">**MRTK_Pulse_ArticulatedHandMeshPurple.mat**</span><span class="sxs-lookup"><span data-stu-id="91a01-113">**MRTK_Pulse_ArticulatedHandMeshPurple.mat**</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="91a01-114">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="91a01-114">Prerequisites</span></span>

<span data-ttu-id="91a01-115">Stellen Sie für das Beispiel für räumliches Netz sicher, dass MRTK_Pulse_SpatialMeshBlue.mat oder MRTK_Pulse_SpatialMeshPurple.mat unter MixedRealityToolkit-Objekt -> Spatial Awareness Profile -> Display Einstellungen -> Visible Material zugewiesen ist.</span><span class="sxs-lookup"><span data-stu-id="91a01-115">For the spatial mesh example, ensure that MRTK_Pulse_SpatialMeshBlue.mat or MRTK_Pulse_SpatialMeshPurple.mat is assigned under MixedRealityToolkit object -> Spatial Awareness Profile -> Display Settings -> Visible Material.</span></span>

<span data-ttu-id="91a01-116">Stellen Sie für das Handgitterbeispiel sicher, dass MRTK_Pulse_ArticulatedHandMeshBlue.mat oder MRTK_Pulse_ArticulatedHandMeshPurple.mat in ArticulatedHandMesh.prefab zugewiesen ist, das selbst in MRTK Einstellungen -> Input -> Hand Tracking -> Hand Mesh Prefab zugewiesen werden sollte.</span><span class="sxs-lookup"><span data-stu-id="91a01-116">For the hand mesh example, ensure that MRTK_Pulse_ArticulatedHandMeshBlue.mat or MRTK_Pulse_ArticulatedHandMeshPurple.mat is assigned in ArticulatedHandMesh.prefab, which itself should be assigned in MRTK Settings -> Input -> Hand Tracking -> Hand Mesh Prefab.</span></span>

## <a name="how-it-works"></a><span data-ttu-id="91a01-117">Funktionsweise</span><span class="sxs-lookup"><span data-stu-id="91a01-117">How it works</span></span>

<span data-ttu-id="91a01-118">Der Handgitter-Shader verwendet UVs, um den Puls entlang des Handgitters zu ordnen und die Hand zu ausblenden.</span><span class="sxs-lookup"><span data-stu-id="91a01-118">The hand mesh shader uses UVs to map the pulse along the hand mesh, and to fade out the wrist.</span></span> <span data-ttu-id="91a01-119">Der Oberflächenrekonstruktions-Shader verwendet die Scheitelpunktpositionen, um den Puls zu zuordnen.</span><span class="sxs-lookup"><span data-stu-id="91a01-119">The surface reconstruction shader uses the vertex positions to map the pulse.</span></span>

## <a name="spatial-mesh-example---pulseshaderspatialmeshexampleunity"></a><span data-ttu-id="91a01-120">Spatial Mesh-Beispiel: PulseShaderSpatialMeshExample.unity</span><span class="sxs-lookup"><span data-stu-id="91a01-120">Spatial Mesh Example - PulseShaderSpatialMeshExample.unity</span></span>

<span data-ttu-id="91a01-121">Ähnlich wie HoloLens 2 Shell-Erfahrung können Sie mit dem Handstrahl in die Luft tippen und zeigen, um einen pulsenden Effekt auf das räumliche Netz zu erzeugen.</span><span class="sxs-lookup"><span data-stu-id="91a01-121">Similar to HoloLens 2's shell experience, you can point and air-tap with the hand ray to generate a pulsing effect on the spatial mesh.</span></span> <span data-ttu-id="91a01-122">Die Beispielszene enthält das ExampleSpatialMesh-Objekt, bei dem es sich um ein Testobjekt für räumliche Gittermodelldaten für den Unity-Spielmodus handelt.</span><span class="sxs-lookup"><span data-stu-id="91a01-122">The example scene contains ExampleSpatialMesh object which is a test spatial mesh data for Unity's game mode.</span></span> <span data-ttu-id="91a01-123">Dieses Objekt wird deaktiviert und auf dem Gerät ausgeblendet.</span><span class="sxs-lookup"><span data-stu-id="91a01-123">This object will be disabled and hidden on the device.</span></span>

<span data-ttu-id="91a01-124">**Das Skript PulseShaderSpatialMeshHandler.cs** generiert den Pulse-Effekt auf das räumliche Netz an der Trefferpunktposition, wenn `PulseOnSelect` true ist.</span><span class="sxs-lookup"><span data-stu-id="91a01-124">**PulseShaderSpatialMeshHandler.cs** script generates the pulse effect on the spatial mesh at the hit point position if `PulseOnSelect` is true.</span></span> <span data-ttu-id="91a01-125">Die -Eigenschaft kann auch im Material selbst für eine sich wiederholende Animation auf  `Auto Pulse` TRUE festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="91a01-125">The  `Auto Pulse` property can also be set to true in the material itself for a repeating animation.</span></span>  <span data-ttu-id="91a01-126">In der Beispielszene wird dieses Skript an das PulseShaderSpatialMeshParent-Prefab angefügt.</span><span class="sxs-lookup"><span data-stu-id="91a01-126">In the example scene, this script is attached to the PulseShaderSpatialMeshParent prefab.</span></span>  <span data-ttu-id="91a01-127">Auf dieses Prefab wird unter der Spatial Awareness Profile through Runtime Spatial Mesh Prefab-Eigenschaft verwiesen.</span><span class="sxs-lookup"><span data-stu-id="91a01-127">This prefab is referenced under the Spatial Awareness Profile through Runtime Spatial Mesh Prefab property.</span></span> <span data-ttu-id="91a01-128">Zur Laufzeit wird das PulseShaderSpatialMeshParent-Prefab instanziiert und der Hierarchie räumlicher Gitternetze hinzugefügt (dieses Verhalten kann nur auf dem Gerät im Editor nicht beobachtet werden).</span><span class="sxs-lookup"><span data-stu-id="91a01-128">During runtime, the PulseShaderSpatialMeshParent prefab and is instantiated and added to the spatial mesh hierarchy (only on device, this behavior cannot be observed in the editor).</span></span>

## <a name="hand-mesh-example---pulseshaderhandmeshexampleunity"></a><span data-ttu-id="91a01-129">Hand Mesh-Beispiel: PulseShaderHandMeshExample.unity</span><span class="sxs-lookup"><span data-stu-id="91a01-129">Hand Mesh Example - PulseShaderHandMeshExample.unity</span></span>

<span data-ttu-id="91a01-130">Diese Beispielszene veranschaulicht die Handgittervisualisierung mithilfe eines Pulse Shaders.</span><span class="sxs-lookup"><span data-stu-id="91a01-130">This example scene demonstrates the hand mesh visualization using pulse shader.</span></span> <span data-ttu-id="91a01-131">Wenn eine Hand vom Gerät erkannt HoloLens gerät, wird die Pulse-Animation einmal ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="91a01-131">When a hand is detected by the HoloLens device, pulse animation will be triggered once.</span></span> <span data-ttu-id="91a01-132">Dieses visuelle Feedback kann die Interaktionsvertrauen des Benutzers erhöhen.</span><span class="sxs-lookup"><span data-stu-id="91a01-132">This visual feedback can increase the user's interaction confidence.</span></span> 

<span data-ttu-id="91a01-133">**Das Skript PulseShaderHandMeshHandler.cs** generiert pulse effect auf das zugewiesene Material.</span><span class="sxs-lookup"><span data-stu-id="91a01-133">**PulseShaderHandMeshHandler.cs** script generates pulse effect on the assigned material.</span></span> <span data-ttu-id="91a01-134">Standardmäßig ist "Pulse On Hand Detected" aktiviert.</span><span class="sxs-lookup"><span data-stu-id="91a01-134">By default, 'Pulse On Hand Detected' is checked.</span></span>
