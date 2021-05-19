---
title: Nachverfolgungsdienst unterbrochen
description: Übersicht über den LostTracking-Dienst in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 96090b05c60cfaa6ff5d8c5e1dc7a58cc2658b71
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144527"
---
# <a name="lost-tracking-visualization"></a><span data-ttu-id="3f1ee-104">Visualisierung für verlorene Nachverfolgung</span><span class="sxs-lookup"><span data-stu-id="3f1ee-104">Lost tracking visualization</span></span>

![Verlorene Nachverfolgung](../images/lost-tracking/LostTrackingVisualization.jpg)

<span data-ttu-id="3f1ee-106">Der Erweiterungsdienst für verlorene Nachverfolgung stellt animierte HoloLens-Shellstilvisu visuals für den verlorenen Nachverfolgungszustand zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="3f1ee-106">Lost Tracking Extension Service provides HoloLens shell style animated visual for the lost tracking state.</span></span>

## <a name="how-to-use-lost-tracking-extensions"></a><span data-ttu-id="3f1ee-107">Verwenden verloren gegangener Nachverfolgungserweiterungen</span><span class="sxs-lookup"><span data-stu-id="3f1ee-107">How to use lost tracking extensions</span></span>

<span data-ttu-id="3f1ee-108">Fügen Sie im MRTK-Profil den Erweiterungen **den** Dienst für verlorene Nachverfolgung hinzu.</span><span class="sxs-lookup"><span data-stu-id="3f1ee-108">In MRTK Profile, add **Lost Tracking Service** to the Extensions.</span></span> <span data-ttu-id="3f1ee-109">Weisen **Sie DefaultLostTrackingServiceProfile zu,** einschließlich **LostTrackingVisualPrefab.**</span><span class="sxs-lookup"><span data-stu-id="3f1ee-109">Assign **DefaultLostTrackingServiceProfile** which includes **LostTrackingVisualPrefab**.</span></span>

<img src="../images/lost-tracking/LostTracking_Extensions.png" width="550" alt="Lost Tracking Extension">
