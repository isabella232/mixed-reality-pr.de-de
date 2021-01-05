---
title: Hand- und Bewegungscontroller
description: Erfahren Sie mehr über die Interaktionsmodelle von Handlern und Bewegungs Controllern, die die Grenze zwischen dem virtuellen und dem physischen entfernen können.
author: shengkait
ms.author: shentan
ms.date: 04/26/2019
ms.topic: article
keywords: Gemischte Realität, Hände, Bewegungs Controller, Interaktion, Entwurf, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, hololens, mrtk, Mixed Reality Toolkit
ms.openlocfilehash: 1dffdd5f3471993dfdb5e504e4c5b87ec0bfef7d
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847326"
---
# <a name="hands-and-motion-controllers"></a><span data-ttu-id="17a7e-104">Hand- und Bewegungscontroller</span><span class="sxs-lookup"><span data-stu-id="17a7e-104">Hands and motion controllers</span></span>

## <a name="scenarios"></a><span data-ttu-id="17a7e-105">Szenarien</span><span class="sxs-lookup"><span data-stu-id="17a7e-105">Scenarios</span></span>

<span data-ttu-id="17a7e-106">Nachdem Sie die [Interaktions Übersicht](interaction-fundamentals.md)gelesen haben, wählen Sie das Hand-und Motion Controller-Interaktionsmodell aus.</span><span class="sxs-lookup"><span data-stu-id="17a7e-106">After reading the [interaction overview](interaction-fundamentals.md), you choose the hand and motion controller interaction model.</span></span> <span data-ttu-id="17a7e-107">Dies bedeutet, dass Sie eine Anwendung entwickeln, die es Benutzern ermöglicht, zwei Hände für die Interaktion mit der Holographic World zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="17a7e-107">This means you're developing an application requiring users to use two hands to interact with the holographic world.</span></span> <span data-ttu-id="17a7e-108">Ihre Anwendung wird das Ziel erreichen, die Grenze zwischen virtuellen und physischen zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="17a7e-108">Your application is going to achieve the goal of removing the boundary between virtual and physical.</span></span>

<span data-ttu-id="17a7e-109">Einige spezifische Szenarien können wie folgt lauten:</span><span class="sxs-lookup"><span data-stu-id="17a7e-109">Some specific scenarios might be:</span></span>
* <span data-ttu-id="17a7e-110">Bereitstellen von virtuellen 2D-Bildschirmen für Information Worker mit Angeboten zum Anzeigen und Steuern von Inhalten auf der Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="17a7e-110">Providing information workers 2D virtual screens with UI affordances to display and control content</span></span>
* <span data-ttu-id="17a7e-111">Bereitstellen von Tutorials und Handbüchern für die erste zeilige Worker für die Factory</span><span class="sxs-lookup"><span data-stu-id="17a7e-111">Providing first line workers tutorials and guides for factory assembly lines</span></span>
* <span data-ttu-id="17a7e-112">Entwickeln von professionellen Werkzeugen für die Unterstützung und Ausbildung von Medizinern</span><span class="sxs-lookup"><span data-stu-id="17a7e-112">Developing professional tools for assisting and educating medical professionals</span></span>  
* <span data-ttu-id="17a7e-113">Verwenden von virtuellen 3D-Objekten zum Schmücken der Realwelt oder zum Erstellen einer zweiten Welt</span><span class="sxs-lookup"><span data-stu-id="17a7e-113">Using 3D virtual objects to decorate the real world or to create a second world</span></span> 
* <span data-ttu-id="17a7e-114">Erstellen von standortbezogenen Diensten und Spielen, die die Realwelt als Hintergrund verwenden</span><span class="sxs-lookup"><span data-stu-id="17a7e-114">Creating location-based services and games using the real world as a background</span></span>

<br>

---

## <a name="hands-and-motion-controllers-modalities"></a><span data-ttu-id="17a7e-115">Methoden der Hands-und Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="17a7e-115">Hands and motion controllers modalities</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="17a7e-116">[![Direkte Manipulation mit den Händen](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)</span><span class="sxs-lookup"><span data-stu-id="17a7e-116">[![Direct manipulation with hands](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)</span></span><br>
       ### <a name="direct-manipulation-with-handsbr"></a>[<span data-ttu-id="17a7e-117">Direkte Manipulation mit den Händen</span><span class="sxs-lookup"><span data-stu-id="17a7e-117">Direct manipulation with hands</span></span>](direct-manipulation.md)<br>
       <span data-ttu-id="17a7e-118">Modalität, die die Leistungsfähigkeit anwendet, die Benutzer verwenden können, um Hologramme zu berühren und zu bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="17a7e-118">Modality applying the power of hands that users can use to touch and manipulate holograms.</span></span> <span data-ttu-id="17a7e-119">Mithilfe der täglichen Lebensdauer und der Bereitstellung geeigneter visueller Visualisierungen können Benutzer die gleiche Art und Weise verwenden, um reale Objekte so zu manipulieren, dass Sie mit virtuellen Anwendungen interagieren.</span><span class="sxs-lookup"><span data-stu-id="17a7e-119">By using daily life experiences and providing proper visual affordances, users can use the same way of manipulating real world objects to interact with virtual ones.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="17a7e-120">[![Zeigen und Bestätigen mit den Händen](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)</span><span class="sxs-lookup"><span data-stu-id="17a7e-120">[![Point and commit with hands](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)</span></span><br>
        ### <a name="point-and-commit-with-handsbr"></a>[<span data-ttu-id="17a7e-121">Zeigen und Ausführen mit den Händen</span><span class="sxs-lookup"><span data-stu-id="17a7e-121">Point and commit with hands</span></span>](point-and-commit.md)<br>
        <span data-ttu-id="17a7e-122">Diese Modalität ermöglicht es Benutzern, mit holograms in einer Distanz zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="17a7e-122">This modality empowers users to interact with holograms in a distance.</span></span> <span data-ttu-id="17a7e-123">Sie ermöglicht es Benutzern, die Umgebung optimal zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="17a7e-123">It enables users to make the best use of surroundings.</span></span> <span data-ttu-id="17a7e-124">Benutzer können holograms überall platzieren und aus beliebigen Entfernungen darauf zugreifen.</span><span class="sxs-lookup"><span data-stu-id="17a7e-124">Users can place holograms anywhere and still access them from any distance.</span></span> <span data-ttu-id="17a7e-125">Die mentalen Modelle und Gesten zum Steuern und manipulieren von 2D-und 3D-holograms sind stark synchron mit denen der direkten Bearbeitung.</span><span class="sxs-lookup"><span data-stu-id="17a7e-125">The mental models and gestures for controlling and manipulating 2D and 3D holograms are highly in sync with those of direct manipulation.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="17a7e-126">[![Bewegungscontroller](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)</span><span class="sxs-lookup"><span data-stu-id="17a7e-126">[![Motion controllers](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)</span></span><br>
       ### <a name="motion-controllersbr"></a>[<span data-ttu-id="17a7e-127">Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="17a7e-127">Motion controllers</span></span>](motion-controllers.md)<br>
       <span data-ttu-id="17a7e-128">Bewegungs Controller erweitern die physischen Funktionen des Benutzers durch exakte Interaktionen über einen Bereich von Entfernungen bei der Verwendung von einem oder beiden Händen.</span><span class="sxs-lookup"><span data-stu-id="17a7e-128">Motion controllers extend the user's physical capabilities with precise interactions across a range of distances while using one or both hands.</span></span> <span data-ttu-id="17a7e-129">Diese Hardware Zubehör bieten Verknüpfungen zu vielen häufig verwendeten Interaktionen und stellen ein sicheres, taktiles Feedback für verschiedene Aktionen bereit.</span><span class="sxs-lookup"><span data-stu-id="17a7e-129">These hardware accessories provide shortcuts to many commonly used interactions and provide sure-footed, tactile feedback for various actions.</span></span> <span data-ttu-id="17a7e-130">Derzeit sind Motion-Controller nur für Windows Mixed Reality-Szenarios (WMR) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="17a7e-130">Currently, motion controllers are only available for Windows Mixed Reality (WMR) scenarios.</span></span> 
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="17a7e-131">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="17a7e-131">See also</span></span>
* [<span data-ttu-id="17a7e-132">Anvisieren mit dem Kopf und Ausführen</span><span class="sxs-lookup"><span data-stu-id="17a7e-132">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="17a7e-133">Anvisieren mit dem Kopf und Verweilen</span><span class="sxs-lookup"><span data-stu-id="17a7e-133">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="17a7e-134">Direkte Manipulation mit den Händen</span><span class="sxs-lookup"><span data-stu-id="17a7e-134">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="17a7e-135">Zeigen und Ausführen mit den Händen</span><span class="sxs-lookup"><span data-stu-id="17a7e-135">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="17a7e-136">Freihändig</span><span class="sxs-lookup"><span data-stu-id="17a7e-136">Hands-free</span></span>](hands-free.md)
