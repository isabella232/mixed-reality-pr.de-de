---
title: Anvisieren und Verweilen
description: Allgemeine Übersicht über den (Augen-/Schreib-) Blick und das Eingangs Modell
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: Gemischte Realität, Blick, wohnen, Interaktion, Entwurf, Augen Verfolgung, Head-Tracking, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, hololens, mrtk, Mixed Reality Toolkit
ms.openlocfilehash: d47401b65f7d62e1fe59655c42efe72ac68acfc6
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94702196"
---
# <a name="gaze-and-dwell"></a><span data-ttu-id="8a2de-104">Anvisieren und Verweilen</span><span class="sxs-lookup"><span data-stu-id="8a2de-104">Gaze and dwell</span></span>

<span data-ttu-id="8a2de-105">Wenn die Hände mit Werkzeugen und Gegenständen beschäftigt sind, können Gesten mühsam oder unmöglich sein.</span><span class="sxs-lookup"><span data-stu-id="8a2de-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span>
<span data-ttu-id="8a2de-106">Sprachbefehle können in bestimmten Kontexten auch unzuverlässig sein, z. b. unter übermäßig Laute Bedingungen.</span><span class="sxs-lookup"><span data-stu-id="8a2de-106">Voice commands may also be unreliable in certain contexts, for example under excessively loud conditions.</span></span>
<span data-ttu-id="8a2de-107">"Blick" und "Wohnen" bietet einen vertrauten und leicht zu erarbeitenden Mechanismus für das Arbeiten mit den hololens und Freihand.</span><span class="sxs-lookup"><span data-stu-id="8a2de-107">Gaze and dwell offers a familiar and easy-to-master mechanism for working heads-up and hands-free on HoloLens.</span></span>
<span data-ttu-id="8a2de-108">Außerdem ist "Blick" und "Wohnen" ein hervorragend Fall Back, das von Rausch Störungen oder Ruhe Einschränkungen in der Betriebsumgebung unabhängig ist.</span><span class="sxs-lookup"><span data-stu-id="8a2de-108">Additionally, gaze and dwell is a great fallback which is independent of noise interference or silence constraints in the operating environment.</span></span>
<span data-ttu-id="8a2de-109">Wir unterscheiden zwei Varianten von _Blick und wohnen_: [Kopf-und](gaze-and-dwell-head.md) [Einblicken](gaze-and-dwell-eyes.md)und wohnen.</span><span class="sxs-lookup"><span data-stu-id="8a2de-109">We distinguish two variants of _gaze and dwell_: [Head-gaze and dwell](gaze-and-dwell-head.md) and [Eye-gaze and dwell](gaze-and-dwell-eyes.md).</span></span>

## <a name="scenarios"></a><span data-ttu-id="8a2de-110">Szenarien</span><span class="sxs-lookup"><span data-stu-id="8a2de-110">Scenarios</span></span>

<span data-ttu-id="8a2de-111">Der Blick und das Leben sind hervorragend in Szenarios, in denen die Hände einer Person mit anderen Aufgaben beschäftigt sind, und die Stimme ist aufgrund von Umwelt-oder sozialen Einschränkungen nicht 100% zuverlässig oder verfügbar.</span><span class="sxs-lookup"><span data-stu-id="8a2de-111">Gaze and dwell excels in scenarios where a person's hands are busy with other tasks, and voice isn't 100% reliable or available due to environmental or social constraints.</span></span>
<span data-ttu-id="8a2de-112">Ein gutes Beispiel ist eine Person, die eine HoloLens trägt, um Referenzinformationen bei der Reparatur eines Fahrzeugmotors zu überlagern.</span><span class="sxs-lookup"><span data-stu-id="8a2de-112">A good example is a person wearing a HoloLens to overlay reference information while repairing a car engine.</span></span>
<span data-ttu-id="8a2de-113">Die Hände sind mit Werkzeugen beschäftigt oder stützen den eigenen Körper, während sich die Person in den Motorraum lehnt.</span><span class="sxs-lookup"><span data-stu-id="8a2de-113">Their hands are busy with tools or supporting their body as they lean into the engine compartment.</span></span>
<span data-ttu-id="8a2de-114">Der Garagenbereich ist laut, mit einem ständigen Klopfen und Knarren der Werkzeuge, wodurch sich die Verwendung von Sprachbefehlen schwierig gestaltet.</span><span class="sxs-lookup"><span data-stu-id="8a2de-114">The garage space is loud, with the constant banging and buzzing of tools, making voice commands difficult.</span></span>
<span data-ttu-id="8a2de-115">"Blick" und "Wohnen" ermöglicht es der Person, die die hololens verwendet, sicher zu navigieren, ohne den Workflow zu unterbrechen.</span><span class="sxs-lookup"><span data-stu-id="8a2de-115">Gaze and dwell allows the person using the HoloLens to confidently navigate their reference material without interrupting their workflow.</span></span>

## <a name="device-support"></a><span data-ttu-id="8a2de-116">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="8a2de-116">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="8a2de-117"><strong>Eingabemodell</strong></span><span class="sxs-lookup"><span data-stu-id="8a2de-117"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="8a2de-118"><a href="../hololens-hardware-details.md"><strong>HoloLens (1. Generation)</strong></a></span><span class="sxs-lookup"><span data-stu-id="8a2de-118"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="8a2de-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="8a2de-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="8a2de-120"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="8a2de-120"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="8a2de-121">Anvisieren mit dem Kopf und Verweilen</span><span class="sxs-lookup"><span data-stu-id="8a2de-121">Head-gaze and dwell</span></span></td>
        <td><span data-ttu-id="8a2de-122">✔️ Empfohlen</span><span class="sxs-lookup"><span data-stu-id="8a2de-122">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="8a2de-123">✔️ Empfohlen</span><span class="sxs-lookup"><span data-stu-id="8a2de-123">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="8a2de-124">✔️ Empfohlen</span><span class="sxs-lookup"><span data-stu-id="8a2de-124">✔️ Recommended</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="8a2de-125">Anvisieren und Verweilen</span><span class="sxs-lookup"><span data-stu-id="8a2de-125">Eye-gaze and dwell</span></span></td>
        <td><span data-ttu-id="8a2de-126">❌ Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="8a2de-126">❌ Not available</span></span></td>
        <td><span data-ttu-id="8a2de-127">✔️ Empfohlen</span><span class="sxs-lookup"><span data-stu-id="8a2de-127">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="8a2de-128">❌ Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="8a2de-128">❌ Not available</span></span></td>
    </tr>
</table>


<br>

---

 ## <a name="see-also"></a><span data-ttu-id="8a2de-129">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="8a2de-129">See also</span></span>
* [<span data-ttu-id="8a2de-130">Augenbasierte Interaktion</span><span class="sxs-lookup"><span data-stu-id="8a2de-130">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="8a2de-131">Blickverfolgung auf HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="8a2de-131">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="8a2de-132">Anvisieren und Ausführen</span><span class="sxs-lookup"><span data-stu-id="8a2de-132">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="8a2de-133">Hände – Direkte Manipulation</span><span class="sxs-lookup"><span data-stu-id="8a2de-133">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="8a2de-134">Hände – Gesten</span><span class="sxs-lookup"><span data-stu-id="8a2de-134">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="8a2de-135">Hände – Zeigen und Ausführen</span><span class="sxs-lookup"><span data-stu-id="8a2de-135">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="8a2de-136">Instinktive Interaktionen</span><span class="sxs-lookup"><span data-stu-id="8a2de-136">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="8a2de-137">Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="8a2de-137">Voice input</span></span>](voice-input.md)
