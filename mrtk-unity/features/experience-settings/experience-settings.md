---
title: ExperienceSettings
description: Dokumentation zu den verschiedenen Benutzererfahrungseinstellungen für MRTK
author: RogPodge
ms.author: roliu
ms.date: 04/13/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 1c93e2ee703eb5dad43bb51236b9991d17e1d58d
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647834"
---
# <a name="experience-settings"></a><span data-ttu-id="b5e4c-104">Einstellungen für die Benutzererfahrung</span><span class="sxs-lookup"><span data-stu-id="b5e4c-104">Experience Settings</span></span>

<span data-ttu-id="b5e4c-105">Eine der Herausforderungen beim Erstellen einer Benutzeroberfläche für Mixed Reality ist die Ausrichtung auf verschiedene Benutzeroberflächen.</span><span class="sxs-lookup"><span data-stu-id="b5e4c-105">One of the challenges of creating UI for Mixed Reality is aligning across different experiences.</span></span> <span data-ttu-id="b5e4c-106">Mit DEM MRTK können Sie und für Ihre Szene festlegen und konfigurieren Folgendes, um sich entsprechend der `Target Experience Scale` `Content Offset` Zielskala zu verhalten.</span><span class="sxs-lookup"><span data-stu-id="b5e4c-106">With MRTK, you can set the `Target Experience Scale` and the `Content Offset` for your scene, will configue the following to behave appropriately for the target scale.</span></span>

- <span data-ttu-id="b5e4c-107">Mixed Reality Szeneninhalt</span><span class="sxs-lookup"><span data-stu-id="b5e4c-107">Mixed Reality Scene Content</span></span>
- <span data-ttu-id="b5e4c-108">Begrenzungssystem</span><span class="sxs-lookup"><span data-stu-id="b5e4c-108">Boundary System</span></span>

  ![Erfahrungseinstellungen im MRTK-Konfigurationsprofil](../images/experience-settings/ExperienceSettings.png)

## <a name="target-experience-scale"></a><span data-ttu-id="b5e4c-110">Skalierung der Zielerfahrung</span><span class="sxs-lookup"><span data-stu-id="b5e4c-110">Target Experience Scale</span></span>

<span data-ttu-id="b5e4c-111">Die **Zielumgebungsskala** gibt die Umgebung an, für die die Umgebung entworfen wurde.</span><span class="sxs-lookup"><span data-stu-id="b5e4c-111">The **Target Experience Scale** specifies the environment for which the experience is designed.</span></span> <span data-ttu-id="b5e4c-112">Sie kann die folgenden Werte übernehmen.</span><span class="sxs-lookup"><span data-stu-id="b5e4c-112">It can take on the following values.</span></span>

* <span data-ttu-id="b5e4c-113">*OrientationOnly:* Eine Erfahrung, bei der nur die Headsetausrichtung verwendet und die Schwerkraft ausgerichtet ist.</span><span class="sxs-lookup"><span data-stu-id="b5e4c-113">*OrientationOnly* - An experience which utilizes only the headset orientation and is gravity aligned.</span></span> <span data-ttu-id="b5e4c-114">Der Ursprung des Koordinatensystems befindet sich auf Der Kopfebene.</span><span class="sxs-lookup"><span data-stu-id="b5e4c-114">The coordinate system origin is at head level.</span></span>
* <span data-ttu-id="b5e4c-115">*"Seated":* Eine Beerfahrung, die für die Verwendung mit dem Platz konzipiert ist.</span><span class="sxs-lookup"><span data-stu-id="b5e4c-115">*Seated* - An experience designed for seated use.</span></span> <span data-ttu-id="b5e4c-116">Der Ursprung des Koordinatensystems befindet sich auf Bodenebene.</span><span class="sxs-lookup"><span data-stu-id="b5e4c-116">The coordinate system origin is at floor level.</span></span>
* <span data-ttu-id="b5e4c-117">*Stehend:* Eine Erfahrung, die für den standfesten Einsatz konzipiert ist.</span><span class="sxs-lookup"><span data-stu-id="b5e4c-117">*Standing* - An experience designed for stationary standing use.</span></span> <span data-ttu-id="b5e4c-118">Der Ursprung des Koordinatensystems befindet sich auf Bodenebene.</span><span class="sxs-lookup"><span data-stu-id="b5e4c-118">The coordinate system origin is at floor level.</span></span>
* <span data-ttu-id="b5e4c-119">*Raum:* Eine Erfahrung, die entwickelt wurde, um Bewegungen in einem Raum zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="b5e4c-119">*Room* - An experience designed to support movement throughout a room.</span></span> <span data-ttu-id="b5e4c-120">Der Ursprung des Koordinatensystems befindet sich auf Bodenebene.</span><span class="sxs-lookup"><span data-stu-id="b5e4c-120">The coordinate system origin is at floor level.</span></span>
* <span data-ttu-id="b5e4c-121">*Welt:* Eine Erfahrung, die dafür konzipiert ist, die physische Welt zu nutzen und sich durch diese zu bewegen.</span><span class="sxs-lookup"><span data-stu-id="b5e4c-121">*World* - An experience designed to utilize and move through the physical world.</span></span> <span data-ttu-id="b5e4c-122">Der Ursprung des Koordinatensystems befindet sich auf Der Kopfebene.</span><span class="sxs-lookup"><span data-stu-id="b5e4c-122">The coordinate system origin is at head level.</span></span>

## <a name="content-offset"></a><span data-ttu-id="b5e4c-123">Inhaltsoffset</span><span class="sxs-lookup"><span data-stu-id="b5e4c-123">Content Offset</span></span>

<span data-ttu-id="b5e4c-124">Dieser Parameter gibt die Höhe über [](scene-content.md) dem Boden an, um Mixed Reality Szeneninhalt zu versatzen, wenn **Ausrichtungstyp** auf Ausrichtung mit **Erfahrungsskala festgelegt ist.**</span><span class="sxs-lookup"><span data-stu-id="b5e4c-124">This parameter specifies the height above the floor to offset [Mixed Reality Scene Content](scene-content.md) when **Alignment Type** is set to **Align with Experience Scale**</span></span>