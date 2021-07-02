---
title: Hand-Physikalischer Dienst
description: Dokumentation zur Verwendung des Erweiterungsdiensts "Hand physics" in MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: af7ea753d52b5e478c54ca19d6d8e391401eea6d
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176256"
---
# <a name="hand-physics-service"></a><span data-ttu-id="7c9de-104">Hand-Physikalischer Dienst</span><span class="sxs-lookup"><span data-stu-id="7c9de-104">Hand physics service</span></span>

![Hand Physics Extension Service](../images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)

<span data-ttu-id="7c9de-106">Der Hand-Physikalische Dienst ermöglicht feste Körperkollisionsereignisse und Interaktionen mit artikulierten Händen.</span><span class="sxs-lookup"><span data-stu-id="7c9de-106">The hand physics service enables rigid body collision events and interactions with articulated hands.</span></span>

## <a name="enabling-the-extension"></a><span data-ttu-id="7c9de-107">Aktivieren der Erweiterung</span><span class="sxs-lookup"><span data-stu-id="7c9de-107">Enabling the extension</span></span>

<span data-ttu-id="7c9de-108">Um die Erweiterung zu aktivieren, öffnen Sie Ihr RegisteredServiceProvider-Profil.</span><span class="sxs-lookup"><span data-stu-id="7c9de-108">To enable the extension, open your RegisteredServiceProvider profile.</span></span> <span data-ttu-id="7c9de-109">Klicken Sie `Register a new Service Provider` auf diese Schaltfläche, um eine neue Konfiguration hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="7c9de-109">Click `Register a new Service Provider` to add a new configuration.</span></span> <span data-ttu-id="7c9de-110">Wählen Sie im Feld Komponententyp die Option HandPhysicsService aus.</span><span class="sxs-lookup"><span data-stu-id="7c9de-110">In the component type field, select HandPhysicsService.</span></span> <span data-ttu-id="7c9de-111">Wählen Sie im Feld Konfigurationsprofil das in der Erweiterung enthaltene Standardprofil für die Handmechanik aus.</span><span class="sxs-lookup"><span data-stu-id="7c9de-111">In the configuration Profile field, select the default hand physics profile included with the extension.</span></span>

## <a name="profile-options"></a><span data-ttu-id="7c9de-112">Profiloptionen</span><span class="sxs-lookup"><span data-stu-id="7c9de-112">Profile options</span></span>

### <a name="hand-physics-layer"></a><span data-ttu-id="7c9de-113">Hand-Physikalische Schicht</span><span class="sxs-lookup"><span data-stu-id="7c9de-113">Hand physics layer</span></span>

<span data-ttu-id="7c9de-114">Steuert die Ebene, zu der die instanziierten Handverbindungen gelangen.</span><span class="sxs-lookup"><span data-stu-id="7c9de-114">Controls the layer the instantiated hand joints will go to.</span></span>

<span data-ttu-id="7c9de-115">Während der Dienst standardmäßig die "Standardebene" (0) verwendet, wird empfohlen, eine separate Ebene für Objekte der Handmechanik zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="7c9de-115">While the service defaults to the "default" layer (0), it is recommended to use a separate layer for hand physics objects.</span></span> <span data-ttu-id="7c9de-116">Andernfalls kann es zu unerwünschten Kollisionen und/oder ungenauen Raycasts kommen.</span><span class="sxs-lookup"><span data-stu-id="7c9de-116">Otherwise there may be unwanted collisions and/or inaccurate raycasts.</span></span>

### <a name="finger-tip-kinematic-body-prefab"></a><span data-ttu-id="7c9de-117">Finger tip kinematic body prefab</span><span class="sxs-lookup"><span data-stu-id="7c9de-117">Finger tip kinematic body prefab</span></span>

<span data-ttu-id="7c9de-118">Steuert, welches Prefab auf Fingerspitzen instanziiert wird.</span><span class="sxs-lookup"><span data-stu-id="7c9de-118">Controls which prefab is instantiated on fingertips.</span></span> <span data-ttu-id="7c9de-119">Damit der Dienst wie erwartet funktioniert, erfordert das Prefab Folgendes:</span><span class="sxs-lookup"><span data-stu-id="7c9de-119">In order for the service to work as expected, the prefab requires:</span></span>

- <span data-ttu-id="7c9de-120">Eine starre Komponente, bei der isKinematic aktiviert ist</span><span class="sxs-lookup"><span data-stu-id="7c9de-120">A rigidbody component, with isKinematic enabled</span></span>
- <span data-ttu-id="7c9de-121">Ein Collider</span><span class="sxs-lookup"><span data-stu-id="7c9de-121">A collider</span></span>
- <span data-ttu-id="7c9de-122">`JointKinematicBody`-Komponente</span><span class="sxs-lookup"><span data-stu-id="7c9de-122">`JointKinematicBody` component</span></span>

### <a name="use-palm-kinematic-body"></a><span data-ttu-id="7c9de-123">Verwenden des kinetischen Handflächenkörpers</span><span class="sxs-lookup"><span data-stu-id="7c9de-123">Use palm kinematic body</span></span>

<span data-ttu-id="7c9de-124">Steuert, ob der Dienst versucht, ein Prefab auf der Handfläche zu instanziieren.</span><span class="sxs-lookup"><span data-stu-id="7c9de-124">Controls whether the service will attempt to instantiate a prefab on the palm joint.</span></span>

### <a name="palm-kinematic-body-prefab"></a><span data-ttu-id="7c9de-125">Handflächen-Kinematic Body Prefab</span><span class="sxs-lookup"><span data-stu-id="7c9de-125">Palm kinematic body prefab</span></span>

<span data-ttu-id="7c9de-126">Wenn `UsePalmKinematicBody` aktiviert ist, ist dies das Prefab, das instanziiert wird.</span><span class="sxs-lookup"><span data-stu-id="7c9de-126">When `UsePalmKinematicBody` is enabled, this is the prefab it will instantiate.</span></span> <span data-ttu-id="7c9de-127">Genau wie `FingerTipKinematicBodyPrefab` erfordert dieses Prefab:</span><span class="sxs-lookup"><span data-stu-id="7c9de-127">Just like `FingerTipKinematicBodyPrefab`, this prefab requires:</span></span>

- <span data-ttu-id="7c9de-128">Eine starre Komponente, bei der isKinematic aktiviert ist</span><span class="sxs-lookup"><span data-stu-id="7c9de-128">A rigidbody component, with isKinematic enabled</span></span>
- <span data-ttu-id="7c9de-129">Ein Collider</span><span class="sxs-lookup"><span data-stu-id="7c9de-129">A collider</span></span>
- <span data-ttu-id="7c9de-130">`JointKinematicBody`-Komponente</span><span class="sxs-lookup"><span data-stu-id="7c9de-130">`JointKinematicBody` component</span></span>

## <a name="how-to-use-the-service"></a><span data-ttu-id="7c9de-131">Verwenden des Diensts</span><span class="sxs-lookup"><span data-stu-id="7c9de-131">How to use the service</span></span>

<span data-ttu-id="7c9de-132">Verwenden Sie nach der Aktivierung die -Eigenschaft eines Colliders, `IsTrigger` um Kollisionsereignisse von allen 10 Ziffern (und Handflächen, wenn sie aktiviert sind) zu empfangen.</span><span class="sxs-lookup"><span data-stu-id="7c9de-132">Once enabled, use any collider's `IsTrigger` property to receive collision events from all 10 digits (and palms if they're enabled).</span></span>
