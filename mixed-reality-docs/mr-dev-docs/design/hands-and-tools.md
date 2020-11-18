---
title: Hand- und Bewegungscontroller
description: Erfahren Sie mehr über die Interaktionsmodelle von Handlern und Bewegungs Controllern, die die Grenze zwischen dem virtuellen und dem physischen entfernen können.
author: shengkait
ms.author: shentan
ms.date: 04/26/2019
ms.topic: article
keywords: Gemischte Realität, Hände, Bewegungs Controller, Interaktion, Entwurf, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, hololens, mrtk, Mixed Reality Toolkit
ms.openlocfilehash: e931e5ec11548d9aab0d1dd7f8921dbc7554abab
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94702156"
---
# <a name="hands-and-motion-controllers"></a><span data-ttu-id="157ea-104">Hand- und Bewegungscontroller</span><span class="sxs-lookup"><span data-stu-id="157ea-104">Hands and motion controllers</span></span>
## <a name="scenarios"></a><span data-ttu-id="157ea-105">Szenarien</span><span class="sxs-lookup"><span data-stu-id="157ea-105">Scenarios</span></span>
<span data-ttu-id="157ea-106">Wenn Sie sich entscheiden, dieses Interaktionsmodell nach dem Lesen der [Interaktions Übersicht zu über](interaction-fundamentals.md)nehmen, bedeutet dies, dass Sie eine Anwendung entwickeln, die es Benutzern ermöglicht, zwei Hände für die Interaktion mit der Holographic World zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="157ea-106">If you choose to adopt this interaction model after reading the [interaction overview](interaction-fundamentals.md), it means that you are developing an application requiring users to use two hands to interact with the holographic world.</span></span> <span data-ttu-id="157ea-107">Ihre Anwendung wird das Ziel erreichen, die Grenze zwischen virtuellen und physischen zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="157ea-107">Your application is going to achieve the goal of removing the boundary between virtual and physical.</span></span>

<span data-ttu-id="157ea-108">Einige spezifische Szenarien können wie folgt lauten:</span><span class="sxs-lookup"><span data-stu-id="157ea-108">Some specific scenarios might be:</span></span>
* <span data-ttu-id="157ea-109">Bereitstellen von virtuellen 2D-Bildschirmen für Information Worker mit Angeboten zum Anzeigen und Steuern von Inhalten auf der Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="157ea-109">Providing information workers 2D virtual screens with UI affordances to display and control content</span></span>
* <span data-ttu-id="157ea-110">Bereitstellen von Tutorials und Handbüchern für die erste zeilige Worker für die Factory</span><span class="sxs-lookup"><span data-stu-id="157ea-110">Providing first line workers tutorials and guides for factory assembly lines</span></span>
* <span data-ttu-id="157ea-111">Entwickeln von professionellen Werkzeugen für die Unterstützung und Ausbildung von Medizinern</span><span class="sxs-lookup"><span data-stu-id="157ea-111">Developing professional tools for assisting and educating medical professionals</span></span>  
* <span data-ttu-id="157ea-112">Verwenden von virtuellen 3D-Objekten zum Schmücken der Realwelt oder zum Erstellen einer zweiten Welt</span><span class="sxs-lookup"><span data-stu-id="157ea-112">Using 3D virtual objects to decorate the real world or to create a second world</span></span> 
* <span data-ttu-id="157ea-113">Erstellen von standortbezogenen Diensten und Spielen, die die Realwelt als Hintergrund verwenden</span><span class="sxs-lookup"><span data-stu-id="157ea-113">Creating location-based services and games using the real world as a background</span></span>

<br>

---

## <a name="hands-and-motion-controllers-modalities"></a><span data-ttu-id="157ea-114">Methoden der Hands-und Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="157ea-114">Hands and motion controllers modalities</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="157ea-115">[![Direkte Manipulation mit den Händen](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)</span><span class="sxs-lookup"><span data-stu-id="157ea-115">[![Direct manipulation with hands](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)</span></span><br>
       ### <a name="direct-manipulation-with-handsbr"></a>[<span data-ttu-id="157ea-116">Direkte Manipulation mit den Händen</span><span class="sxs-lookup"><span data-stu-id="157ea-116">Direct manipulation with hands</span></span>](direct-manipulation.md)<br>
       <span data-ttu-id="157ea-117">Dies ist eine Modalität, die die Leistungsfähigkeit nutzt, mit der Benutzer die Hologramme direkt berühren und bearbeiten können.</span><span class="sxs-lookup"><span data-stu-id="157ea-117">This is a modality leveraging the power of hands, with which users are capable of touching and manipulating the holograms directly.</span></span> <span data-ttu-id="157ea-118">Durch die Nutzung von täglichen Erfahrungen und die Bereitstellung geeigneter visueller Visualisierungen können Benutzer die gleiche Art und Weise verwenden, um reale Objekte so zu manipulieren, dass Sie mit virtuellen Anwendungen interagieren.</span><span class="sxs-lookup"><span data-stu-id="157ea-118">By leveraging daily life experiences and providing proper visual affordances, users are able to use the same way of manipulating real world objects to interact with virtual ones.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="157ea-119">[![Zeigen und Ausführen mit den Händen](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)</span><span class="sxs-lookup"><span data-stu-id="157ea-119">[![Point and commit with hands](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)</span></span><br>
        ### <a name="point-and-commit-with-handsbr"></a>[<span data-ttu-id="157ea-120">Zeigen und Ausführen mit den Händen</span><span class="sxs-lookup"><span data-stu-id="157ea-120">Point and commit with hands</span></span>](point-and-commit.md)<br>
        <span data-ttu-id="157ea-121">Diese Modalität ermöglicht es Benutzern, mit holograms in einer Distanz zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="157ea-121">This modality empowers users to interact with holograms in a distance.</span></span> <span data-ttu-id="157ea-122">Sie ermöglicht es Benutzern, die Umgebung optimal zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="157ea-122">It enables users to make the best use of surroundings.</span></span> <span data-ttu-id="157ea-123">Benutzer können holograms überall platzieren und aus beliebigen Entfernungen darauf zugreifen.</span><span class="sxs-lookup"><span data-stu-id="157ea-123">Users can place holograms anywhere and still access them from any distance.</span></span> <span data-ttu-id="157ea-124">Die mentalen Modelle und Gesten zum Steuern und manipulieren von 2D-und 3D-holograms sind stark synchron mit denen der direkten Bearbeitung.</span><span class="sxs-lookup"><span data-stu-id="157ea-124">The mental models and gestures for controlling and manipulating 2D and 3D holograms are highly in sync with those of direct manipulation.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="157ea-125">[![Motion-Controller](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)</span><span class="sxs-lookup"><span data-stu-id="157ea-125">[![Motion controllers](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)</span></span><br>
       ### <a name="motion-controllersbr"></a>[<span data-ttu-id="157ea-126">Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="157ea-126">Motion controllers</span></span>](motion-controllers.md)<br>
       <span data-ttu-id="157ea-127">Bewegungs Controller sind Tools, mit denen die physischen Funktionen des Benutzers erweitert werden, indem genaue Interaktionen über einen großen Bereich von Entfernungen bereitgestellt werden, wenn ein oder beide Hände verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="157ea-127">Motion controllers are tools that extend the user's physical capabilities by providing precise interactions across a large range of distances while using one or both hands.</span></span> <span data-ttu-id="157ea-128">Diese Hardware Zubehör bieten Verknüpfungen zu vielen häufig verwendeten Interaktionen und bieten unterschiedliche Aktionen, die Sie für eine Reihe von Aktionen durchsuchen können.</span><span class="sxs-lookup"><span data-stu-id="157ea-128">These hardware accessories provide shortcuts to many commonly-used interactions and provide surefooted, tactile feedback for a variety of actions.</span></span> <span data-ttu-id="157ea-129">Derzeit sind Motion-Controller nur für Windows Mixed Reality-Szenarios (WMR) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="157ea-129">Currently, motion controllers are only available for Windows Mixed Reality (WMR) scenarios.</span></span> 
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="157ea-130">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="157ea-130">See also</span></span>
* [<span data-ttu-id="157ea-131">Anvisieren mit dem Kopf und Ausführen</span><span class="sxs-lookup"><span data-stu-id="157ea-131">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="157ea-132">Anvisieren mit dem Kopf und Verweilen</span><span class="sxs-lookup"><span data-stu-id="157ea-132">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="157ea-133">Direkte Manipulation mit den Händen</span><span class="sxs-lookup"><span data-stu-id="157ea-133">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="157ea-134">Zeigen und Ausführen mit den Händen</span><span class="sxs-lookup"><span data-stu-id="157ea-134">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="157ea-135">Freihändig</span><span class="sxs-lookup"><span data-stu-id="157ea-135">Hands-free</span></span>](hands-free.md)
