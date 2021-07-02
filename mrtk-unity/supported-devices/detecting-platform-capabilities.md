---
title: Erkennen von Plattformfunktionen
description: Details zu den verschiedenen Funktionen, die vom MRTK unterstützt werden
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Funktionen,
ms.openlocfilehash: 70d320e178f4635d74b5be6a1874eb4254801719
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175525"
---
# <a name="detecting-platform-capabilities"></a><span data-ttu-id="2f2e9-104">Erkennen von Plattformfunktionen</span><span class="sxs-lookup"><span data-stu-id="2f2e9-104">Detecting platform capabilities</span></span>

<span data-ttu-id="2f2e9-105">Eine häufig gestellte Frage zum MRTK besteht darin, zu wissen, welches bestimmte Gerät (z. B. Microsoft HoloLens 2) zum Ausführen einer Anwendung verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="2f2e9-105">A common question asked of the MRTK involves knowing which specific device (ex: Microsoft HoloLens 2) is being used to run an application.</span></span> <span data-ttu-id="2f2e9-106">Das Ermitteln der genauen Hardware kann auf verschiedenen Plattformen eine Herausforderung darstellen.</span><span class="sxs-lookup"><span data-stu-id="2f2e9-106">Identifying the exact hardware can be challenging on different platforms.</span></span> <span data-ttu-id="2f2e9-107">Stattdessen bietet das MRTK eine Möglichkeit, bestimmte Funktionen zur Laufzeit zu identifizieren (z. B. wenn der aktuelle Geräteendpunkt artikulierte Hände unterstützt).</span><span class="sxs-lookup"><span data-stu-id="2f2e9-107">Instead, the MRTK provides a way to identify specific capabilities at runtime, (e.g. if the current device endpoint supports articulated hands).</span></span>

## <a name="capabilities"></a><span data-ttu-id="2f2e9-108">Funktionen</span><span class="sxs-lookup"><span data-stu-id="2f2e9-108">Capabilities</span></span>

<span data-ttu-id="2f2e9-109">Das Mixed Reality Toolkit stellt die -Enumeration bereit, die einen Satz von Funktionen definiert, für die eine Anwendung zur Laufzeit [`MixedRealityCapability`](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability) Abfragen ausführen kann.</span><span class="sxs-lookup"><span data-stu-id="2f2e9-109">The Mixed Reality Toolkit provides the [`MixedRealityCapability`](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability) enumeration, which defines a set of capabilities for which an application can query at runtime.</span></span>

### <a name="input-system-capabilities"></a><span data-ttu-id="2f2e9-110">Eingabesystemfunktionen</span><span class="sxs-lookup"><span data-stu-id="2f2e9-110">Input system capabilities</span></span>

<span data-ttu-id="2f2e9-111">Das MRTK-Standardeingabesystem unterstützt das Abfragen der folgenden Funktionen:</span><span class="sxs-lookup"><span data-stu-id="2f2e9-111">The default MRTK Input System supports querying the following capabilities:</span></span>

| <span data-ttu-id="2f2e9-112">Funktion</span><span class="sxs-lookup"><span data-stu-id="2f2e9-112">Capability</span></span> | <span data-ttu-id="2f2e9-113">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="2f2e9-113">Description</span></span> |
|---|---|
| <span data-ttu-id="2f2e9-114">ArticulatedHand</span><span class="sxs-lookup"><span data-stu-id="2f2e9-114">ArticulatedHand</span></span> | <span data-ttu-id="2f2e9-115">Artikulierte Handeingabe</span><span class="sxs-lookup"><span data-stu-id="2f2e9-115">Articulated hand input</span></span> |
| <span data-ttu-id="2f2e9-116">EyeTracking (Blickverfolgung)</span><span class="sxs-lookup"><span data-stu-id="2f2e9-116">EyeTracking</span></span> | <span data-ttu-id="2f2e9-117">Anvschauung mit den Augen</span><span class="sxs-lookup"><span data-stu-id="2f2e9-117">Eye gaze targeting</span></span> |
| <span data-ttu-id="2f2e9-118">GGVHand</span><span class="sxs-lookup"><span data-stu-id="2f2e9-118">GGVHand</span></span> | <span data-ttu-id="2f2e9-119">Eingabe der Hand "Gaze-Gesture-Voice"</span><span class="sxs-lookup"><span data-stu-id="2f2e9-119">Gaze-Gesture-Voice hand input</span></span> |
| <span data-ttu-id="2f2e9-120">MotionController</span><span class="sxs-lookup"><span data-stu-id="2f2e9-120">MotionController</span></span> | <span data-ttu-id="2f2e9-121">Eingabe des Bewegungscontrollers</span><span class="sxs-lookup"><span data-stu-id="2f2e9-121">Motion controller input</span></span> |
| <span data-ttu-id="2f2e9-122">VoiceCommand</span><span class="sxs-lookup"><span data-stu-id="2f2e9-122">VoiceCommand</span></span> | <span data-ttu-id="2f2e9-123">Sprachbefehle mit app-definierten Schlüsselwörtern</span><span class="sxs-lookup"><span data-stu-id="2f2e9-123">Voice commands using app defined keywords</span></span> |
| <span data-ttu-id="2f2e9-124">VoiceDictation</span><span class="sxs-lookup"><span data-stu-id="2f2e9-124">VoiceDictation</span></span> | <span data-ttu-id="2f2e9-125">Sprach-zu-Text-Diktat</span><span class="sxs-lookup"><span data-stu-id="2f2e9-125">Voice to text dictation</span></span> |

<span data-ttu-id="2f2e9-126">Der folgende Beispielcode überprüft, ob das Eingabesystem einen Datenanbieter mit Unterstützung für artikulierte Hände geladen hat.</span><span class="sxs-lookup"><span data-stu-id="2f2e9-126">The example code below checks to see if the input system has loaded a data provider with support for articulated hands.</span></span>

```c#
bool supportsArticulatedHands = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.InputSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsArticulatedHands = capabilityCheck.CheckCapability(MixedRealityCapability.ArticulatedHand);
}
```

### <a name="spatial-awareness-capabilities"></a><span data-ttu-id="2f2e9-127">Funktionen des räumlichen Bewusstseins</span><span class="sxs-lookup"><span data-stu-id="2f2e9-127">Spatial awareness capabilities</span></span>

<span data-ttu-id="2f2e9-128">Das MRTK Spatial Awareness-Standardsystem unterstützt das Abfragen der folgenden Funktionen:</span><span class="sxs-lookup"><span data-stu-id="2f2e9-128">The default MRTK Spatial Awareness system supports querying the following capabilities:</span></span>

| <span data-ttu-id="2f2e9-129">Funktion</span><span class="sxs-lookup"><span data-stu-id="2f2e9-129">Capability</span></span> | <span data-ttu-id="2f2e9-130">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="2f2e9-130">Description</span></span> |
|---|---|
| <span data-ttu-id="2f2e9-131">SpatialAwarenessMesh</span><span class="sxs-lookup"><span data-stu-id="2f2e9-131">SpatialAwarenessMesh</span></span> | <span data-ttu-id="2f2e9-132">Räumliche Gitternetze</span><span class="sxs-lookup"><span data-stu-id="2f2e9-132">Spatial meshes</span></span> |
| <span data-ttu-id="2f2e9-133">SpatialAwarenessPlane</span><span class="sxs-lookup"><span data-stu-id="2f2e9-133">SpatialAwarenessPlane</span></span> | <span data-ttu-id="2f2e9-134">Räumliche Ebenen</span><span class="sxs-lookup"><span data-stu-id="2f2e9-134">Spatial planes</span></span> |
| <span data-ttu-id="2f2e9-135">SpatialAwarenessPoint</span><span class="sxs-lookup"><span data-stu-id="2f2e9-135">SpatialAwarenessPoint</span></span> | <span data-ttu-id="2f2e9-136">Räumliche Punkte</span><span class="sxs-lookup"><span data-stu-id="2f2e9-136">Spatial points</span></span> |

<span data-ttu-id="2f2e9-137">In diesem Beispiel wird überprüft, ob das Raumbewusstseinssystem einen Datenanbieter mit Unterstützung für räumliche Gitternetze geladen hat.</span><span class="sxs-lookup"><span data-stu-id="2f2e9-137">This example checks to see if the spatial awareness system has loaded a data provider with support for spatial meshes.</span></span>

```c#
bool supportsSpatialMesh = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.SpatialAwarenessSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsSpatialMesh = capabilityCheck.CheckCapability(MixedRealityCapability.SpatialAwarenessMesh);
}
```

## <a name="see-also"></a><span data-ttu-id="2f2e9-138">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="2f2e9-138">See also</span></span>

- [<span data-ttu-id="2f2e9-139">Dokumentation zur IMixedRealityCapabilityCheck-API</span><span class="sxs-lookup"><span data-stu-id="2f2e9-139">IMixedRealityCapabilityCheck API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
- [<span data-ttu-id="2f2e9-140">MixedRealityCapability-Dokumentation</span><span class="sxs-lookup"><span data-stu-id="2f2e9-140">MixedRealityCapability enum documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability)
