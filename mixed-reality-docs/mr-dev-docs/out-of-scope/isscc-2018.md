---
title: Whitepaper zur tiefenkamera-ISSCC 2018
description: Technisches Whitepaper, das die Tiefe Kamera erläutert, die in Project kinect for Azure und der nächsten Version von hololens verwendet werden soll.
author: mattzmsft
ms.author: mazeller
ms.date: 7/5/2018
ms.topic: article
keywords: Event, ISCC, Maschinelles sehen, Forschung, kinect, hololens, Tiefe, TOF
ms.openlocfilehash: b692f9deeb7768e57ab6161b2c356a6610f18ed9
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2020
ms.locfileid: "91691187"
---
# <a name="depth-camera-whitepaper---isscc-2018"></a><span data-ttu-id="789b1-104">Whitepaper zur tiefenkamera-ISSCC 2018</span><span class="sxs-lookup"><span data-stu-id="789b1-104">Depth camera whitepaper - ISSCC 2018</span></span>

<span data-ttu-id="789b1-105">**Title:** 1MPixel 65nm BSI 320mhz Herabstufung des TOF-Bildsensors mit 3,5 μm globalen Auslöse Pixeln und analoger Klassifizierung</span><span class="sxs-lookup"><span data-stu-id="789b1-105">**Title:** 1Mpixel 65nm BSI 320MHz Demodulated TOF Image Sensor with 3.5μm Global Shutter Pixels and Analog Binning</span></span>

<span data-ttu-id="789b1-106">**Mitwirkende:** Cyrus S bamji, Swati Mehta, Barry Thompson, Tamer Elkhatib, Stefan Wurster, Onur Akkaya, Andrew Payne, John godbaz, Mike f Enton, Vijay rajasekaran, Larry Prather, Satya Nagaraja, vishali mugallapu, Dane Snow, Rich McCauley, Mustansir mukadam Iskender AGI, Shaun McCarthy, zhanping Xu, Travis Perry, William Qian, VEI-Han Chan, Prabhu adepu, Gazi Ali, Muneeb Ahmed, Aditya Mukherjee, sheethal Nayak, Dave gampell, Sunil Acharya, Lou kordus, Pat.</span><span class="sxs-lookup"><span data-stu-id="789b1-106">**Contributors:** Cyrus S Bamji, Swati Mehta, Barry Thompson, Tamer Elkhatib, Stefan Wurster, Onur Akkaya, Andrew Payne, John Godbaz, Mike Fenton, Vijay Rajasekaran, Larry Prather, Satya Nagaraja, Vishali Mogallapu, Dane Snow, Rich McCauley, Mustansir Mukadam, Iskender Agi, Shaun McCarthy, Zhanping Xu, Travis Perry, William Qian, Vei-Han Chan, Prabhu Adepu, Gazi Ali, Muneeb Ahmed, Aditya Mukherjee, Sheethal Nayak, Dave Gampell, Sunil Acharya, Lou Kordus, Pat O'Connor</span></span>

<span data-ttu-id="789b1-107">**Präsentiert in ISSCC 2018 und veröffentlicht in ISSCC deg. Tech. Paper, Feb 2018.**</span><span class="sxs-lookup"><span data-stu-id="789b1-107">**Presented at ISSCC 2018 and published in ISSCC Deg. Tech. Papers, Feb 2018.**</span></span>

<span data-ttu-id="789b1-108">C.</span><span class="sxs-lookup"><span data-stu-id="789b1-108">C.</span></span> <span data-ttu-id="789b1-109">Bamji et al., "1MPixel 65nm BSI 320mhz Herabstufung des TOF-Bildsensors mit 3,5 μm globale Auslöse Pixel und analoge Binning" ISSCC deg.</span><span class="sxs-lookup"><span data-stu-id="789b1-109">Bamji et al., “1Mpixel 65nm BSI 320MHz Demodulated TOF Image Sensor with 3.5μm Global Shutter Pixels and Analog Binning,” ISSCC Deg.</span></span> <span data-ttu-id="789b1-110">Technisch.</span><span class="sxs-lookup"><span data-stu-id="789b1-110">Tech.</span></span> <span data-ttu-id="789b1-111">Paper, pp. 94-95, Feb 2018.</span><span class="sxs-lookup"><span data-stu-id="789b1-111">Papers, pp. 94-95, Feb 2018.</span></span> <span data-ttu-id="789b1-112">IEEE-Explorer-Link: https://ieeexplore.ieee.org/document/8310200/</span><span class="sxs-lookup"><span data-stu-id="789b1-112">IEEE Explore Link: https://ieeexplore.ieee.org/document/8310200/</span></span>

<span data-ttu-id="789b1-113">© 2018 IEEE.</span><span class="sxs-lookup"><span data-stu-id="789b1-113">© 2018 IEEE.</span></span> <span data-ttu-id="789b1-114">Die persönliche Nutzung dieses Materials ist zulässig.</span><span class="sxs-lookup"><span data-stu-id="789b1-114">Personal use of this material is permitted.</span></span> <span data-ttu-id="789b1-115">Die Berechtigung von IEEE muss für alle anderen Verwendungen in allen aktuellen oder zukünftigen Medien abgerufen werden. Dies umfasst das erneute Drucken/erneute Veröffentlichen dieses Materials für Werbe-oder Werbezwecke, das Erstellen neuer sammelarbeiten, für den erneuten Verkauf oder die Weiterverteilung an Server oder Listen oder die Wiederverwendung von urheberrechtlich geschützten Komponenten dieser Arbeit in anderen Werken.</span><span class="sxs-lookup"><span data-stu-id="789b1-115">Permission from IEEE must be obtained for all other uses, in any current or future media, including reprinting/republishing this material for advertising or promotional purposes, creating new collective works, for resale or redistribution to servers or lists, or reuse of any copyrighted component of this work in other works.</span></span>

<span data-ttu-id="789b1-116">**Whitepaper**</span><span class="sxs-lookup"><span data-stu-id="789b1-116">**Whitepaper:**</span></span><br>
<span data-ttu-id="789b1-117">![Vorschau des Whitepaper](images/depth-camera-isscc.PNG)</span><span class="sxs-lookup"><span data-stu-id="789b1-117">![Preview of whitepaper](images/depth-camera-isscc.PNG)</span></span><br>
[<span data-ttu-id="789b1-118">Whitepaper zur Download Tiefe Kamera</span><span class="sxs-lookup"><span data-stu-id="789b1-118">Download depth camera whitepaper</span></span>](images/Depth-Camera-ISSCC-2018.pdf)
