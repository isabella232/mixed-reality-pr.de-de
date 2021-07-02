---
title: Dienst für verlorene Nachverfolgung
description: Übersicht über den LostTracking-Dienst in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 70274639326563b1f3c3a2061dcdbf824fd43709
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176227"
---
# <a name="lost-tracking-service"></a><span data-ttu-id="1443b-104">Dienst für verlorene Nachverfolgung</span><span class="sxs-lookup"><span data-stu-id="1443b-104">Lost tracking service</span></span>

![Verlorene Nachverfolgung](../images/lost-tracking/LostTrackingVisualization.jpg)

<span data-ttu-id="1443b-106">Der Nachverfolgungserweiterungsdienst für verlorene HoloLens stellt ein animiertes Visuelles im Shellstil für den verlorenen Nachverfolgungszustand zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="1443b-106">Lost Tracking Extension Service provides HoloLens shell style animated visual for the lost tracking state.</span></span>

## <a name="how-to-use-lost-tracking-extensions"></a><span data-ttu-id="1443b-107">Verwenden verloren gegangener Nachverfolgungserweiterungen</span><span class="sxs-lookup"><span data-stu-id="1443b-107">How to use lost tracking extensions</span></span>

<span data-ttu-id="1443b-108">Fügen Sie im MRTK-Profil den Erweiterungen **den** Dienst für verlorene Nachverfolgung hinzu.</span><span class="sxs-lookup"><span data-stu-id="1443b-108">In MRTK Profile, add **Lost Tracking Service** to the Extensions.</span></span> <span data-ttu-id="1443b-109">Weisen **Sie DefaultLostTrackingServiceProfile zu,** das **LostTrackingVisualPrefab enthält.**</span><span class="sxs-lookup"><span data-stu-id="1443b-109">Assign **DefaultLostTrackingServiceProfile** which includes **LostTrackingVisualPrefab**.</span></span>

<img src="../images/lost-tracking/LostTracking_Extensions.png" width="550" alt="Lost Tracking Extension">
