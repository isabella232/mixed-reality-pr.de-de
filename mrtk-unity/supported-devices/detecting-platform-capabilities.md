---
title: Erkennen vonPlatformCapabilities
description: Details zu den verschiedenen Funktionen, die mrtk unterstützt
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Funktionen,
ms.openlocfilehash: 62e03c6d47deb079d3460759b5c694dd258a7767
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2021
ms.locfileid: "109852371"
---
# <a name="detecting-platform-capabilities"></a><span data-ttu-id="ba933-104">Erkennen von Plattformfunktionen</span><span class="sxs-lookup"><span data-stu-id="ba933-104">Detecting platform capabilities</span></span>

<span data-ttu-id="ba933-105">Eine häufig gestellte Frage des MRTK umfasst das Wissen, welches bestimmte Gerät (z. B. Microsoft HoloLens 2) zum Ausführen einer Anwendung verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="ba933-105">A common question asked of the MRTK involves knowing which specific device (ex: Microsoft HoloLens 2) is being used to run an application.</span></span> <span data-ttu-id="ba933-106">Das Ermitteln der genauen Hardware kann auf verschiedenen Plattformen eine Herausforderung darstellen.</span><span class="sxs-lookup"><span data-stu-id="ba933-106">Identifying the exact hardware can be challenging on different platforms.</span></span> <span data-ttu-id="ba933-107">Stattdessen bietet das MRTK eine Möglichkeit, bestimmte Funktionen zur Laufzeit zu identifizieren (z. B. wenn der aktuelle Geräteendpunkt artikulierte Hände unterstützt).</span><span class="sxs-lookup"><span data-stu-id="ba933-107">Instead, the MRTK provides a way to identify specific capabilities at runtime, (e.g. if the current device endpoint supports articulated hands).</span></span>

## <a name="capabilities"></a><span data-ttu-id="ba933-108">Funktionen</span><span class="sxs-lookup"><span data-stu-id="ba933-108">Capabilities</span></span>

<span data-ttu-id="ba933-109">Das Mixed Reality Toolkit stellt die [`MixedRealityCapability`](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability) -Enumeration bereit, die einen Satz von Funktionen definiert, für die eine Anwendung zur Laufzeit Abfragen ausführen kann.</span><span class="sxs-lookup"><span data-stu-id="ba933-109">The Mixed Reality Toolkit provides the [`MixedRealityCapability`](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability) enumeration, which defines a set of capabilities for which an application can query at runtime.</span></span>

### <a name="input-system-capabilities"></a><span data-ttu-id="ba933-110">Eingabesystemfunktionen</span><span class="sxs-lookup"><span data-stu-id="ba933-110">Input system capabilities</span></span>

<span data-ttu-id="ba933-111">Das MRTK-Standardeingabesystem unterstützt das Abfragen der folgenden Funktionen:</span><span class="sxs-lookup"><span data-stu-id="ba933-111">The default MRTK Input System supports querying the following capabilities:</span></span>

| <span data-ttu-id="ba933-112">Funktion</span><span class="sxs-lookup"><span data-stu-id="ba933-112">Capability</span></span> | <span data-ttu-id="ba933-113">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ba933-113">Description</span></span> |
|---|---|
| <span data-ttu-id="ba933-114">ArticulatedHand</span><span class="sxs-lookup"><span data-stu-id="ba933-114">ArticulatedHand</span></span> | <span data-ttu-id="ba933-115">Artikulierte Handeingabe</span><span class="sxs-lookup"><span data-stu-id="ba933-115">Articulated hand input</span></span> |
| <span data-ttu-id="ba933-116">EyeTracking (Blickverfolgung)</span><span class="sxs-lookup"><span data-stu-id="ba933-116">EyeTracking</span></span> | <span data-ttu-id="ba933-117">Anvisieren mit den Augen</span><span class="sxs-lookup"><span data-stu-id="ba933-117">Eye gaze targeting</span></span> |
| <span data-ttu-id="ba933-118">GGVHand</span><span class="sxs-lookup"><span data-stu-id="ba933-118">GGVHand</span></span> | <span data-ttu-id="ba933-119">Handeingabe mit Anv-Gesten-Stimme</span><span class="sxs-lookup"><span data-stu-id="ba933-119">Gaze-Gesture-Voice hand input</span></span> |
| <span data-ttu-id="ba933-120">MotionController</span><span class="sxs-lookup"><span data-stu-id="ba933-120">MotionController</span></span> | <span data-ttu-id="ba933-121">Motion Controller-Eingabe</span><span class="sxs-lookup"><span data-stu-id="ba933-121">Motion controller input</span></span> |
| <span data-ttu-id="ba933-122">VoiceCommand</span><span class="sxs-lookup"><span data-stu-id="ba933-122">VoiceCommand</span></span> | <span data-ttu-id="ba933-123">Sprachbefehle mit von der App definierten Schlüsselwörtern</span><span class="sxs-lookup"><span data-stu-id="ba933-123">Voice commands using app defined keywords</span></span> |
| <span data-ttu-id="ba933-124">VoiceDictation</span><span class="sxs-lookup"><span data-stu-id="ba933-124">VoiceDictation</span></span> | <span data-ttu-id="ba933-125">Sprach-zu-Text-Diktat</span><span class="sxs-lookup"><span data-stu-id="ba933-125">Voice to text dictation</span></span> |

<span data-ttu-id="ba933-126">Der folgende Beispielcode überprüft, ob das Eingabesystem einen Datenanbieter mit Unterstützung für artikulierte Hände geladen hat.</span><span class="sxs-lookup"><span data-stu-id="ba933-126">The example code below checks to see if the input system has loaded a data provider with support for articulated hands.</span></span>

```c#
bool supportsArticulatedHands = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.InputSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsArticulatedHands = capabilityCheck.CheckCapability(MixedRealityCapability.ArticulatedHand);
}
```

### <a name="spatial-awareness-capabilities"></a><span data-ttu-id="ba933-127">Funktionen des räumlichen Bewusstseins</span><span class="sxs-lookup"><span data-stu-id="ba933-127">Spatial awareness capabilities</span></span>

<span data-ttu-id="ba933-128">Das MRTK Spatial Awareness-Standardsystem unterstützt das Abfragen der folgenden Funktionen:</span><span class="sxs-lookup"><span data-stu-id="ba933-128">The default MRTK Spatial Awareness system supports querying the following capabilities:</span></span>

| <span data-ttu-id="ba933-129">Funktion</span><span class="sxs-lookup"><span data-stu-id="ba933-129">Capability</span></span> | <span data-ttu-id="ba933-130">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ba933-130">Description</span></span> |
|---|---|
| <span data-ttu-id="ba933-131">SpatialAwarenessMesh</span><span class="sxs-lookup"><span data-stu-id="ba933-131">SpatialAwarenessMesh</span></span> | <span data-ttu-id="ba933-132">Räumliche Gitternetze</span><span class="sxs-lookup"><span data-stu-id="ba933-132">Spatial meshes</span></span> |
| <span data-ttu-id="ba933-133">SpatialAwarenessPlane</span><span class="sxs-lookup"><span data-stu-id="ba933-133">SpatialAwarenessPlane</span></span> | <span data-ttu-id="ba933-134">Räumliche Ebenen</span><span class="sxs-lookup"><span data-stu-id="ba933-134">Spatial planes</span></span> |
| <span data-ttu-id="ba933-135">SpatialAwarenessPoint</span><span class="sxs-lookup"><span data-stu-id="ba933-135">SpatialAwarenessPoint</span></span> | <span data-ttu-id="ba933-136">Räumliche Punkte</span><span class="sxs-lookup"><span data-stu-id="ba933-136">Spatial points</span></span> |

<span data-ttu-id="ba933-137">In diesem Beispiel wird überprüft, ob das Raumbewusstseinssystem einen Datenanbieter mit Unterstützung für räumliche Gitternetze geladen hat.</span><span class="sxs-lookup"><span data-stu-id="ba933-137">This example checks to see if the spatial awareness system has loaded a data provider with support for spatial meshes.</span></span>

```c#
bool supportsSpatialMesh = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.SpatialAwarenessSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsSpatialMesh = capabilityCheck.CheckCapability(MixedRealityCapability.SpatialAwarenessMesh);
}
```

## <a name="see-also"></a><span data-ttu-id="ba933-138">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="ba933-138">See also</span></span>

- [<span data-ttu-id="ba933-139">Dokumentation zur IMixedRealityCapabilityCheck-API</span><span class="sxs-lookup"><span data-stu-id="ba933-139">IMixedRealityCapabilityCheck API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
- [<span data-ttu-id="ba933-140">MixedRealityCapability-Dokumentation</span><span class="sxs-lookup"><span data-stu-id="ba933-140">MixedRealityCapability enum documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability)
