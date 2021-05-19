---
title: Hand Physics Extension Service
description: description Hand Physics-Erweiterungsdienste.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 401a9d31ed3fbbe0c3e02cb95ffebb024f882fd9
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143438"
---
# <a name="hand-physics-extension-services"></a><span data-ttu-id="4f18c-104">Hand-Physikalische Erweiterungsdienste</span><span class="sxs-lookup"><span data-stu-id="4f18c-104">Hand physics extension services</span></span>

<span data-ttu-id="4f18c-105">Der Hand-Physikalische Dienst ermöglicht feste Körperkollisionsereignisse und Interaktionen mit artikulierten Händen.</span><span class="sxs-lookup"><span data-stu-id="4f18c-105">The hand physics service enables rigid body collision events and interactions with articulated hands.</span></span>

## <a name="getting-started-with-hand-physics-extension-service"></a><span data-ttu-id="4f18c-106">Erste Schritte mit dem Erweiterungsdienst für die Handmechanik</span><span class="sxs-lookup"><span data-stu-id="4f18c-106">Getting started with hand physics extension service</span></span>

<span data-ttu-id="4f18c-107">Fügen Sie der Liste der Erweiterungsdienste den Hand-Physikalischen Dienst hinzu, und verwenden Sie das Standardprofil.</span><span class="sxs-lookup"><span data-stu-id="4f18c-107">Add the hand physics service to the list of extension services and use the default profile.</span></span>

<span data-ttu-id="4f18c-108">Verwenden Sie nach der Aktivierung die IsTrigger-Eigenschaft eines Colliders, um Kollisionsereignisse von allen 10 Ziffern (und Handflächen, wenn sie aktiviert sind) zu empfangen.</span><span class="sxs-lookup"><span data-stu-id="4f18c-108">Once enabled, use any collider's IsTrigger property to receive collision events from all 10 digits (and palms if they're enabled).</span></span>

### <a name="prerequisites"></a><span data-ttu-id="4f18c-109">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="4f18c-109">Prerequisites</span></span>

- <span data-ttu-id="4f18c-110">Aktivieren des Erweiterungsdiensts</span><span class="sxs-lookup"><span data-stu-id="4f18c-110">Enabled the extension service</span></span>
- <span data-ttu-id="4f18c-111">Weisen Sie dem Finger/Handflächen-Fugen ein geeignetes Prefab zu.</span><span class="sxs-lookup"><span data-stu-id="4f18c-111">Assign an appropriate prefab to the finger/palm joint.</span></span>

## <a name="recommendations"></a><span data-ttu-id="4f18c-112">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="4f18c-112">Recommendations</span></span>

<span data-ttu-id="4f18c-113">Der Dienst verwendet standardmäßig die Standardebene, es wird jedoch empfohlen, eine separate Ebene für HandPhysics-Objekte zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="4f18c-113">While the service defaults to the "default" layer, it is recommended to use a separate layer for HandPhysics objects.</span></span> <span data-ttu-id="4f18c-114">Andernfalls kann es zu unerwünschten Kollisionen und/oder ungenauen Raycasts kommen.</span><span class="sxs-lookup"><span data-stu-id="4f18c-114">Otherwise there may be unwanted collisions and/or inaccurate raycasts.</span></span>
