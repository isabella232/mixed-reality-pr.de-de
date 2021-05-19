---
title: Erkennen von Plattformfunktionen
description: Details zu den verschiedenen Funktionen, die mrtk unterstützt
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Funktionen,
ms.openlocfilehash: e6f5a70120b2634a4c8c75cdca3d8b369967c4b0
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143859"
---
# <a name="detecting-platform-capabilities"></a><span data-ttu-id="e6b6b-104">Erkennen von Plattformfunktionen</span><span class="sxs-lookup"><span data-stu-id="e6b6b-104">Detecting platform capabilities</span></span>

<span data-ttu-id="e6b6b-105">Eine häufig gestellte Frage des MRTK umfasst das Wissen, welches bestimmte Gerät (z. B. Microsoft HoloLens 2) zum Ausführen einer Anwendung verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="e6b6b-105">A common question asked of the MRTK involves knowing which specific device (ex: Microsoft HoloLens 2) is being used to run an application.</span></span> <span data-ttu-id="e6b6b-106">Das Ermitteln der genauen Hardware kann auf verschiedenen Plattformen eine Herausforderung darstellen.</span><span class="sxs-lookup"><span data-stu-id="e6b6b-106">Identifying the exact hardware can be challenging on different platforms.</span></span> <span data-ttu-id="e6b6b-107">Stattdessen bietet das MRTK eine Möglichkeit, bestimmte Funktionen zur Laufzeit zu identifizieren (z. B. wenn der aktuelle Geräteendpunkt artikulierte Hände unterstützt).</span><span class="sxs-lookup"><span data-stu-id="e6b6b-107">Instead, the MRTK provides a way to identify specific capabilities at runtime, (e.g. if the current device endpoint supports articulated hands).</span></span>

## <a name="capabilities"></a><span data-ttu-id="e6b6b-108">Funktionen</span><span class="sxs-lookup"><span data-stu-id="e6b6b-108">Capabilities</span></span>

<span data-ttu-id="e6b6b-109">Das Mixed Reality Toolkit stellt die [`MixedRealityCapability`](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability) -Enumeration bereit, die einen Satz von Funktionen definiert, für die eine Anwendung zur Laufzeit Abfragen ausführen kann.</span><span class="sxs-lookup"><span data-stu-id="e6b6b-109">The Mixed Reality Toolkit provides the [`MixedRealityCapability`](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability) enumeration, which defines a set of capabilities for which an application can query at runtime.</span></span>

### <a name="input-system-capabilities"></a><span data-ttu-id="e6b6b-110">Eingabesystemfunktionen</span><span class="sxs-lookup"><span data-stu-id="e6b6b-110">Input system capabilities</span></span>

<span data-ttu-id="e6b6b-111">Das STANDARDMÄßIGE MRTK-Eingabesystem unterstützt das Abfragen der folgenden Funktionen:</span><span class="sxs-lookup"><span data-stu-id="e6b6b-111">The default MRTK Input System supports querying the following capabilities:</span></span>

| <span data-ttu-id="e6b6b-112">Funktion</span><span class="sxs-lookup"><span data-stu-id="e6b6b-112">Capability</span></span> | <span data-ttu-id="e6b6b-113">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e6b6b-113">Description</span></span> |
|---|---|
| <span data-ttu-id="e6b6b-114">ArticulatedHand</span><span class="sxs-lookup"><span data-stu-id="e6b6b-114">ArticulatedHand</span></span> | <span data-ttu-id="e6b6b-115">Artikulierte Handeingabe</span><span class="sxs-lookup"><span data-stu-id="e6b6b-115">Articulated hand input</span></span> |
| <span data-ttu-id="e6b6b-116">EyeTracking (Blickverfolgung)</span><span class="sxs-lookup"><span data-stu-id="e6b6b-116">EyeTracking</span></span> | <span data-ttu-id="e6b6b-117">Anvisieren mit den Augen</span><span class="sxs-lookup"><span data-stu-id="e6b6b-117">Eye gaze targeting</span></span> |
| <span data-ttu-id="e6b6b-118">GGVHand</span><span class="sxs-lookup"><span data-stu-id="e6b6b-118">GGVHand</span></span> | <span data-ttu-id="e6b6b-119">Handeingabe mit Anv-Geste-Stimme</span><span class="sxs-lookup"><span data-stu-id="e6b6b-119">Gaze-Gesture-Voice hand input</span></span> |
| <span data-ttu-id="e6b6b-120">MotionController</span><span class="sxs-lookup"><span data-stu-id="e6b6b-120">MotionController</span></span> | <span data-ttu-id="e6b6b-121">Motion Controller-Eingabe</span><span class="sxs-lookup"><span data-stu-id="e6b6b-121">Motion controller input</span></span> |
| <span data-ttu-id="e6b6b-122">VoiceCommand</span><span class="sxs-lookup"><span data-stu-id="e6b6b-122">VoiceCommand</span></span> | <span data-ttu-id="e6b6b-123">Sprachbefehle mit von der App definierten Schlüsselwörtern</span><span class="sxs-lookup"><span data-stu-id="e6b6b-123">Voice commands using app defined keywords</span></span> |
| <span data-ttu-id="e6b6b-124">VoiceDictation</span><span class="sxs-lookup"><span data-stu-id="e6b6b-124">VoiceDictation</span></span> | <span data-ttu-id="e6b6b-125">Sprach-zu-Text-Diktat</span><span class="sxs-lookup"><span data-stu-id="e6b6b-125">Voice to text dictation</span></span> |

<span data-ttu-id="e6b6b-126">Der folgende Beispielcode überprüft, ob das Eingabesystem einen Datenanbieter mit Unterstützung für artikulierte Hände geladen hat.</span><span class="sxs-lookup"><span data-stu-id="e6b6b-126">The example code below checks to see if the input system has loaded a data provider with support for articulated hands.</span></span>

```c#
bool supportsArticulatedHands = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.InputSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsArticulatedHands = capabilityCheck.CheckCapability(MixedRealityCapability.ArticulatedHand);
}
```

### <a name="spatial-awareness-capabilities"></a><span data-ttu-id="e6b6b-127">Funktionen des räumlichen Bewusstseins</span><span class="sxs-lookup"><span data-stu-id="e6b6b-127">Spatial awareness capabilities</span></span>

<span data-ttu-id="e6b6b-128">Das MRTK Spatial Awareness-Standardsystem unterstützt das Abfragen der folgenden Funktionen:</span><span class="sxs-lookup"><span data-stu-id="e6b6b-128">The default MRTK Spatial Awareness system supports querying the following capabilities:</span></span>

| <span data-ttu-id="e6b6b-129">Funktion</span><span class="sxs-lookup"><span data-stu-id="e6b6b-129">Capability</span></span> | <span data-ttu-id="e6b6b-130">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e6b6b-130">Description</span></span> |
|---|---|
| <span data-ttu-id="e6b6b-131">SpatialAwarenessMesh</span><span class="sxs-lookup"><span data-stu-id="e6b6b-131">SpatialAwarenessMesh</span></span> | <span data-ttu-id="e6b6b-132">Räumliche Gitternetze</span><span class="sxs-lookup"><span data-stu-id="e6b6b-132">Spatial meshes</span></span> |
| <span data-ttu-id="e6b6b-133">SpatialAwarenessPlane</span><span class="sxs-lookup"><span data-stu-id="e6b6b-133">SpatialAwarenessPlane</span></span> | <span data-ttu-id="e6b6b-134">Räumliche Ebenen</span><span class="sxs-lookup"><span data-stu-id="e6b6b-134">Spatial planes</span></span> |
| <span data-ttu-id="e6b6b-135">SpatialAwarenessPoint</span><span class="sxs-lookup"><span data-stu-id="e6b6b-135">SpatialAwarenessPoint</span></span> | <span data-ttu-id="e6b6b-136">Räumliche Punkte</span><span class="sxs-lookup"><span data-stu-id="e6b6b-136">Spatial points</span></span> |

<span data-ttu-id="e6b6b-137">In diesem Beispiel wird überprüft, ob das Raumbewusstseinssystem einen Datenanbieter mit Unterstützung für räumliche Gitternetze geladen hat.</span><span class="sxs-lookup"><span data-stu-id="e6b6b-137">This example checks to see if the spatial awareness system has loaded a data provider with support for spatial meshes.</span></span>

```c#
bool supportsSpatialMesh = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.SpatialAwarenessSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsSpatialMesh = capabilityCheck.CheckCapability(MixedRealityCapability.SpatialAwarenessMesh);
}
```

## <a name="see-also"></a><span data-ttu-id="e6b6b-138">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e6b6b-138">See also</span></span>

- [<span data-ttu-id="e6b6b-139">Dokumentation zur IMixedRealityCapabilityCheck-API</span><span class="sxs-lookup"><span data-stu-id="e6b6b-139">IMixedRealityCapabilityCheck API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
- [<span data-ttu-id="e6b6b-140">MixedRealityCapability-Dokumentation</span><span class="sxs-lookup"><span data-stu-id="e6b6b-140">MixedRealityCapability enum documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability)
