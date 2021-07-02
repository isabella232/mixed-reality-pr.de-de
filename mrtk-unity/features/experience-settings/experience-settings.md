---
title: Einstellungen für die Benutzererfahrung
description: Dokumentation zu den verschiedenen Benutzererfahrungseinstellungen für MRTK
author: RogPodge
ms.author: roliu
ms.date: 04/13/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: ab3a449b064d4a1c8f2bf76154f7a25c688693e1
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177357"
---
# <a name="experience-settings"></a><span data-ttu-id="8492e-104">Einstellungen für die Benutzererfahrung</span><span class="sxs-lookup"><span data-stu-id="8492e-104">Experience settings</span></span>

<span data-ttu-id="8492e-105">Eine der Herausforderungen beim Erstellen einer Benutzeroberfläche für Mixed Reality ist die Ausrichtung auf verschiedene Benutzeroberflächen.</span><span class="sxs-lookup"><span data-stu-id="8492e-105">One of the challenges of creating UI for Mixed Reality is aligning across different experiences.</span></span> <span data-ttu-id="8492e-106">Mit MRTK können Sie und für Ihre Szene festlegen und konfigurieren Folgendes, um sich entsprechend der `Target Experience Scale` `Content Offset` Zielskala zu verhalten.</span><span class="sxs-lookup"><span data-stu-id="8492e-106">With MRTK, you can set the `Target Experience Scale` and the `Content Offset` for your scene, will configue the following to behave appropriately for the target scale.</span></span>

- <span data-ttu-id="8492e-107">Mixed Reality Szeneninhalt</span><span class="sxs-lookup"><span data-stu-id="8492e-107">Mixed Reality Scene Content</span></span>
- <span data-ttu-id="8492e-108">Begrenzungssystem</span><span class="sxs-lookup"><span data-stu-id="8492e-108">Boundary System</span></span>

  ![Erfahrung Einstellungen im MRTK-Konfigurationsprofil](../images/experience-settings/ExperienceSettings.png)

## <a name="target-experience-scale"></a><span data-ttu-id="8492e-110">Skalierung der Zielerfahrung</span><span class="sxs-lookup"><span data-stu-id="8492e-110">Target Experience Scale</span></span>

<span data-ttu-id="8492e-111">Die **Zielumgebungsskala** gibt die Umgebung an, für die die Umgebung entworfen wurde.</span><span class="sxs-lookup"><span data-stu-id="8492e-111">The **Target Experience Scale** specifies the environment for which the experience is designed.</span></span> <span data-ttu-id="8492e-112">Sie kann die folgenden Werte übernehmen.</span><span class="sxs-lookup"><span data-stu-id="8492e-112">It can take on the following values.</span></span>

* <span data-ttu-id="8492e-113">*OrientationOnly:* Eine Erfahrung, bei der nur die Headsetausrichtung verwendet und die Schwerkraft ausgerichtet ist.</span><span class="sxs-lookup"><span data-stu-id="8492e-113">*OrientationOnly* - An experience which utilizes only the headset orientation and is gravity aligned.</span></span> <span data-ttu-id="8492e-114">Der Ursprung des Koordinatensystems befindet sich auf Der Kopfebene.</span><span class="sxs-lookup"><span data-stu-id="8492e-114">The coordinate system origin is at head level.</span></span>
* <span data-ttu-id="8492e-115">*"Seated":* Eine Beerfahrung, die für die Verwendung mit dem Platz konzipiert ist.</span><span class="sxs-lookup"><span data-stu-id="8492e-115">*Seated* - An experience designed for seated use.</span></span> <span data-ttu-id="8492e-116">Der Ursprung des Koordinatensystems befindet sich auf Bodenebene.</span><span class="sxs-lookup"><span data-stu-id="8492e-116">The coordinate system origin is at floor level.</span></span>
* <span data-ttu-id="8492e-117">*Stehend:* Eine Erfahrung, die für den standfesten Einsatz konzipiert ist.</span><span class="sxs-lookup"><span data-stu-id="8492e-117">*Standing* - An experience designed for stationary standing use.</span></span> <span data-ttu-id="8492e-118">Der Ursprung des Koordinatensystems befindet sich auf Bodenebene.</span><span class="sxs-lookup"><span data-stu-id="8492e-118">The coordinate system origin is at floor level.</span></span>
* <span data-ttu-id="8492e-119">*Raum:* Eine Erfahrung, die entwickelt wurde, um Bewegungen in einem Raum zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="8492e-119">*Room* - An experience designed to support movement throughout a room.</span></span> <span data-ttu-id="8492e-120">Der Ursprung des Koordinatensystems befindet sich auf Bodenebene.</span><span class="sxs-lookup"><span data-stu-id="8492e-120">The coordinate system origin is at floor level.</span></span>
* <span data-ttu-id="8492e-121">*Welt:* Eine Erfahrung, die dafür konzipiert ist, die physische Welt zu nutzen und sich durch diese zu bewegen.</span><span class="sxs-lookup"><span data-stu-id="8492e-121">*World* - An experience designed to utilize and move through the physical world.</span></span> <span data-ttu-id="8492e-122">Der Ursprung des Koordinatensystems befindet sich auf Der Kopfebene.</span><span class="sxs-lookup"><span data-stu-id="8492e-122">The coordinate system origin is at head level.</span></span>

## <a name="content-offset"></a><span data-ttu-id="8492e-123">Inhaltsoffset</span><span class="sxs-lookup"><span data-stu-id="8492e-123">Content Offset</span></span>

<span data-ttu-id="8492e-124">Dieser Parameter gibt die Höhe über [](scene-content.md) dem Boden an, um Mixed Reality Szeneninhalt zu versatzen, wenn **Ausrichtungstyp** auf Ausrichtung an Der **Erfahrungsskala ausgerichtet ist.**</span><span class="sxs-lookup"><span data-stu-id="8492e-124">This parameter specifies the height above the floor to offset [Mixed Reality Scene Content](scene-content.md) when **Alignment Type** is set to **Align with Experience Scale**</span></span>
