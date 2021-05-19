---
title: 'Szenensystem: Beleuchtung von Szenen'
description: Dokumentation zur Beleuchtung in der Szene.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: fa7442bc968710a31ce3ca379c7fd73928e6e324
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144416"
---
# <a name="lighting-scene-operations"></a><span data-ttu-id="0b2e1-104">Beleuchtungsszenenvorgänge</span><span class="sxs-lookup"><span data-stu-id="0b2e1-104">Lighting scene operations</span></span>

<span data-ttu-id="0b2e1-105">Die in Ihrem Profil definierte Standardbeleuchtungsszene wird beim Start geladen.</span><span class="sxs-lookup"><span data-stu-id="0b2e1-105">The default lighting scene defined in your profile is loaded on startup.</span></span> <span data-ttu-id="0b2e1-106">Diese Beleuchtungsszene bleibt geladen, bis `SetLightingScene` aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="0b2e1-106">That lighting scene remains loaded until `SetLightingScene` is called.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

sceneSystem.SetLightingScene("MorningLighting");
```

## <a name="lighting-setting-transitions"></a><span data-ttu-id="0b2e1-107">Lichteinstellungsübergänge</span><span class="sxs-lookup"><span data-stu-id="0b2e1-107">Lighting setting transitions</span></span>

<span data-ttu-id="0b2e1-108">`transitionType` steuert den Stil des Übergangs zur neuen Beleuchtungsszene.</span><span class="sxs-lookup"><span data-stu-id="0b2e1-108">`transitionType` controls the style of the transition to new lighting scene.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

sceneSystem.SetLightingScene("MiddayLighting", LightingSceneTransitionType.CrossFade);
```

<span data-ttu-id="0b2e1-109">Die verfügbaren Stile sind:</span><span class="sxs-lookup"><span data-stu-id="0b2e1-109">The available styles are:</span></span>

<span data-ttu-id="0b2e1-110">type</span><span class="sxs-lookup"><span data-stu-id="0b2e1-110">Type</span></span> | <span data-ttu-id="0b2e1-111">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="0b2e1-111">Description</span></span> | <span data-ttu-id="0b2e1-112">Duration</span><span class="sxs-lookup"><span data-stu-id="0b2e1-112">Duration</span></span>
--- | --- | ---
<span data-ttu-id="0b2e1-113">Keiner</span><span class="sxs-lookup"><span data-stu-id="0b2e1-113">None</span></span> | <span data-ttu-id="0b2e1-114">Vorherige Beleuchtungsszene wird entladen, neue Beleuchtungsszene wird geladen.</span><span class="sxs-lookup"><span data-stu-id="0b2e1-114">Previous lighting scene is unloaded, new lighting scene is loaded.</span></span> <span data-ttu-id="0b2e1-115">Kein Übergang.</span><span class="sxs-lookup"><span data-stu-id="0b2e1-115">No transition.</span></span> | <span data-ttu-id="0b2e1-116">Wird ignoriert.</span><span class="sxs-lookup"><span data-stu-id="0b2e1-116">Ignored</span></span>
<span data-ttu-id="0b2e1-117">FadeToBlack</span><span class="sxs-lookup"><span data-stu-id="0b2e1-117">FadeToBlack</span></span> | <span data-ttu-id="0b2e1-118">Die vorherige Beleuchtungsszene wird in Schwarz ausgeblendet.</span><span class="sxs-lookup"><span data-stu-id="0b2e1-118">Previous lighting scene fades out to black.</span></span> <span data-ttu-id="0b2e1-119">Neue Beleuchtungsszene wird geladen und dann von Schwarz ausgeblendet.</span><span class="sxs-lookup"><span data-stu-id="0b2e1-119">New lighting scene is loaded, then faded up from black.</span></span> <span data-ttu-id="0b2e1-120">Nützlich für reibungslose Übergänge zwischen Standorten.</span><span class="sxs-lookup"><span data-stu-id="0b2e1-120">Useful for smooth transitions between locations.</span></span> | <span data-ttu-id="0b2e1-121">Verwendet</span><span class="sxs-lookup"><span data-stu-id="0b2e1-121">Used</span></span>
<span data-ttu-id="0b2e1-122">Überblenden</span><span class="sxs-lookup"><span data-stu-id="0b2e1-122">CrossFade</span></span> | <span data-ttu-id="0b2e1-123">Die vorherige Beleuchtungsszene wird ausgeblendet, wenn eine neue Beleuchtungsszene einblendet.</span><span class="sxs-lookup"><span data-stu-id="0b2e1-123">Previous lighting scene fades out as new lighting scene fades in.</span></span> <span data-ttu-id="0b2e1-124">Nützlich für reibungslose Übergänge zwischen Beleuchtungssetups am gleichen Standort.</span><span class="sxs-lookup"><span data-stu-id="0b2e1-124">Useful for smooth transitions between lighting setups in the same location.</span></span> | <span data-ttu-id="0b2e1-125">Verwendet</span><span class="sxs-lookup"><span data-stu-id="0b2e1-125">Used</span></span>

<span data-ttu-id="0b2e1-126">Beachten Sie, dass einige Beleuchtungseinstellungen während Übergängen nicht interpoliert werden können.</span><span class="sxs-lookup"><span data-stu-id="0b2e1-126">Note that some lighting settings cannot be interpolated during transitions.</span></span> <span data-ttu-id="0b2e1-127">Wenn Sie einen reibungslosen visuellen Übergang wünschen, müssen diese Einstellungen zwischen den Beleuchtungsszenen konsistent bleiben.</span><span class="sxs-lookup"><span data-stu-id="0b2e1-127">If you want a smooth visual transition these settings will have to remain consistent between lighting scenes.</span></span>

<span data-ttu-id="0b2e1-128">Einstellung</span><span class="sxs-lookup"><span data-stu-id="0b2e1-128">Setting</span></span> | <span data-ttu-id="0b2e1-129">Smooth FadeToBlack-Übergang</span><span class="sxs-lookup"><span data-stu-id="0b2e1-129">Smooth FadeToBlack Transition</span></span> | <span data-ttu-id="0b2e1-130">Reibungsloser CrossFade-Übergang</span><span class="sxs-lookup"><span data-stu-id="0b2e1-130">Smooth CrossFade Transition</span></span>
--- | --- | ---
<span data-ttu-id="0b2e1-131">Skybox</span><span class="sxs-lookup"><span data-stu-id="0b2e1-131">Skybox</span></span> | <span data-ttu-id="0b2e1-132">Nein</span><span class="sxs-lookup"><span data-stu-id="0b2e1-132">No</span></span> | <span data-ttu-id="0b2e1-133">Nein</span><span class="sxs-lookup"><span data-stu-id="0b2e1-133">No</span></span>
<span data-ttu-id="0b2e1-134">Benutzerdefinierte Reflektionen</span><span class="sxs-lookup"><span data-stu-id="0b2e1-134">Custom Reflections</span></span> | <span data-ttu-id="0b2e1-135">Nein</span><span class="sxs-lookup"><span data-stu-id="0b2e1-135">No</span></span> | <span data-ttu-id="0b2e1-136">Nein</span><span class="sxs-lookup"><span data-stu-id="0b2e1-136">No</span></span>
<span data-ttu-id="0b2e1-137">Sonnenlicht– Echtzeitschatten</span><span class="sxs-lookup"><span data-stu-id="0b2e1-137">Sun light realtime shadows</span></span> | <span data-ttu-id="0b2e1-138">Ja</span><span class="sxs-lookup"><span data-stu-id="0b2e1-138">Yes</span></span> | <span data-ttu-id="0b2e1-139">Nein</span><span class="sxs-lookup"><span data-stu-id="0b2e1-139">No</span></span>
