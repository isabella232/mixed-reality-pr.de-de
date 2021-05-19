---
title: Übersicht über den Hand physics-Dienst
description: Dokumentation zur Verwendung des Hand-Physics-Erweiterungsdiensts in MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 751aec148d3a40da4728d2fdd60a60402b59a4de
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145082"
---
# <a name="hand-physics-extension-service"></a><span data-ttu-id="e5b5e-104">Hand physikalischer Erweiterungsdienst</span><span class="sxs-lookup"><span data-stu-id="e5b5e-104">Hand physics extension service</span></span>

![Hand Physics Extension Service](../images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)

<span data-ttu-id="e5b5e-106">Der Hand physikalischer Dienst ermöglicht feste Körperkollisionsereignisse und Interaktionen mit artikulierten Händen.</span><span class="sxs-lookup"><span data-stu-id="e5b5e-106">The hand physics service enables rigid body collision events and interactions with articulated hands.</span></span>

## <a name="enabling-the-extension"></a><span data-ttu-id="e5b5e-107">Aktivieren der Erweiterung</span><span class="sxs-lookup"><span data-stu-id="e5b5e-107">Enabling the extension</span></span>

<span data-ttu-id="e5b5e-108">Um die Erweiterung zu aktivieren, öffnen Sie Ihr RegisteredServiceProvider-Profil.</span><span class="sxs-lookup"><span data-stu-id="e5b5e-108">To enable the extension, open your RegisteredServiceProvider profile.</span></span> <span data-ttu-id="e5b5e-109">Klicken `Register a new Service Provider` Sie auf diese Schaltfläche, um eine neue Konfiguration hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="e5b5e-109">Click `Register a new Service Provider` to add a new configuration.</span></span> <span data-ttu-id="e5b5e-110">Wählen Sie im Feld Komponententyp die Option HandPhysicsService aus.</span><span class="sxs-lookup"><span data-stu-id="e5b5e-110">In the component type field, select HandPhysicsService.</span></span> <span data-ttu-id="e5b5e-111">Wählen Sie im Feld Konfigurationsprofil das standardmäßige Hand-Physics-Profil aus, das in der Erweiterung enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="e5b5e-111">In the configuration Profile field, select the default hand physics profile included with the extension.</span></span>

## <a name="profile-options"></a><span data-ttu-id="e5b5e-112">Profiloptionen</span><span class="sxs-lookup"><span data-stu-id="e5b5e-112">Profile options</span></span>

### <a name="hand-physics-layer"></a><span data-ttu-id="e5b5e-113">Hand physics layer (Hand-Physik-Schicht)</span><span class="sxs-lookup"><span data-stu-id="e5b5e-113">Hand physics layer</span></span>

<span data-ttu-id="e5b5e-114">Steuert die Ebene, zu der die instanziierten Handgelenke wechseln.</span><span class="sxs-lookup"><span data-stu-id="e5b5e-114">Controls the layer the instantiated hand joints will go to.</span></span>

<span data-ttu-id="e5b5e-115">Während der Dienst standardmäßig auf die "Standardebene" (0) festgelegt ist, wird empfohlen, eine separate Ebene für Handkörperobjekte zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="e5b5e-115">While the service defaults to the "default" layer (0), it is recommended to use a separate layer for hand physics objects.</span></span> <span data-ttu-id="e5b5e-116">Andernfalls kann es zu unerwünschten Kollisionen und/oder ungenauen Raycasts gekommen sein.</span><span class="sxs-lookup"><span data-stu-id="e5b5e-116">Otherwise there may be unwanted collisions and/or inaccurate raycasts.</span></span>

### <a name="finger-tip-kinematic-body-prefab"></a><span data-ttu-id="e5b5e-117">Kinematisches Körper-Prefab für Fingerspitzen</span><span class="sxs-lookup"><span data-stu-id="e5b5e-117">Finger tip kinematic body prefab</span></span>

<span data-ttu-id="e5b5e-118">Steuert, welches Prefab an Fingerspitzen instanziiert wird.</span><span class="sxs-lookup"><span data-stu-id="e5b5e-118">Controls which prefab is instantiated on fingertips.</span></span> <span data-ttu-id="e5b5e-119">Damit der Dienst wie erwartet funktioniert, erfordert das Prefab:</span><span class="sxs-lookup"><span data-stu-id="e5b5e-119">In order for the service to work as expected, the prefab requires:</span></span>

- <span data-ttu-id="e5b5e-120">Eine Festkörperkomponente, bei der isKinematic aktiviert ist</span><span class="sxs-lookup"><span data-stu-id="e5b5e-120">A rigidbody component, with isKinematic enabled</span></span>
- <span data-ttu-id="e5b5e-121">Ein Collider</span><span class="sxs-lookup"><span data-stu-id="e5b5e-121">A collider</span></span>
- <span data-ttu-id="e5b5e-122">`JointKinematicBody`-Komponente</span><span class="sxs-lookup"><span data-stu-id="e5b5e-122">`JointKinematicBody` component</span></span>

### <a name="use-palm-kinematic-body"></a><span data-ttu-id="e5b5e-123">Verwenden des kinematischen Handflächenkörpers</span><span class="sxs-lookup"><span data-stu-id="e5b5e-123">Use palm kinematic body</span></span>

<span data-ttu-id="e5b5e-124">Steuert, ob der Dienst versucht, ein Prefab auf der Handfläche zu instanziieren.</span><span class="sxs-lookup"><span data-stu-id="e5b5e-124">Controls whether the service will attempt to instantiate a prefab on the palm joint.</span></span>

### <a name="palm-kinematic-body-prefab"></a><span data-ttu-id="e5b5e-125">Wad kinematic body prefab</span><span class="sxs-lookup"><span data-stu-id="e5b5e-125">Palm kinematic body prefab</span></span>

<span data-ttu-id="e5b5e-126">Wenn `UsePalmKinematicBody` aktiviert ist, ist dies das Prefab, das instanziiert wird.</span><span class="sxs-lookup"><span data-stu-id="e5b5e-126">When `UsePalmKinematicBody` is enabled, this is the prefab it will instantiate.</span></span> <span data-ttu-id="e5b5e-127">Genau wie `FingerTipKinematicBodyPrefab` erfordert dieses Prefab:</span><span class="sxs-lookup"><span data-stu-id="e5b5e-127">Just like `FingerTipKinematicBodyPrefab`, this prefab requires:</span></span>

- <span data-ttu-id="e5b5e-128">Eine starre Komponente, bei der isKinematic aktiviert ist</span><span class="sxs-lookup"><span data-stu-id="e5b5e-128">A rigidbody component, with isKinematic enabled</span></span>
- <span data-ttu-id="e5b5e-129">Ein Collider</span><span class="sxs-lookup"><span data-stu-id="e5b5e-129">A collider</span></span>
- <span data-ttu-id="e5b5e-130">`JointKinematicBody`-Komponente</span><span class="sxs-lookup"><span data-stu-id="e5b5e-130">`JointKinematicBody` component</span></span>

## <a name="how-to-use-the-service"></a><span data-ttu-id="e5b5e-131">Verwenden des Diensts</span><span class="sxs-lookup"><span data-stu-id="e5b5e-131">How to use the service</span></span>

<span data-ttu-id="e5b5e-132">Verwenden Sie nach der Aktivierung die -Eigenschaft eines Colliders, `IsTrigger` um Kollisionsereignisse von allen 10 Ziffern (und Handflächen, wenn sie aktiviert sind) zu empfangen.</span><span class="sxs-lookup"><span data-stu-id="e5b5e-132">Once enabled, use any collider's `IsTrigger` property to receive collision events from all 10 digits (and palms if they're enabled).</span></span>
