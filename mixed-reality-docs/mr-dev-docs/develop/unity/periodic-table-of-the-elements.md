---
title: Periodensystem der Elemente
description: Die periodische Tabelle der Elemente ist eine Open-Source-Beispiel-App aus den Mixed Reality-Entwurfs Labs von Microsoft. Erfahren Sie, wie Sie mithilfe einer Objektsammlung ein Array von Objekten im 3D-Raum mit verschiedenen Oberflächentypen anordnen können.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Gemischte Windows-Realität, Design, Beispiel-APP, Steuerelemente, mrtk, Mixed Reality Toolkit, Unity, Beispiel-apps, Beispiel-apps, Open Source, Microsoft Store, hololens, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: a4099c889fee886e63d3a8b773398a250621f26e
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010181"
---
# <a name="periodic-table-of-the-elements"></a><span data-ttu-id="aa236-105">Periodensystem der Elemente</span><span class="sxs-lookup"><span data-stu-id="aa236-105">Periodic Table of the Elements</span></span>

>[!NOTE]
><span data-ttu-id="aa236-106">In diesem Artikel wird ein exploratives Beispiel erläutert, das wir in den [Entwurfs Labors für gemischte Realität](https://github.com/Microsoft/MRDesignLabs_Unity)erstellt haben, einem Ort, an dem wir unsere Erkenntnisse und Vorschläge für die Entwicklung gemischter Reality-apps teilen.</span><span class="sxs-lookup"><span data-stu-id="aa236-106">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="aa236-107">Unsere Entwurfs bezogenen Artikel und Code werden sich weiterentwickeln, wenn wir neue Ermittlungen durchführen.</span><span class="sxs-lookup"><span data-stu-id="aa236-107">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="aa236-108">[Die periodische Tabelle der Elemente](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) ist eine Open-Source-Beispiel-App aus den Mixed Reality-Entwurfs Labs von Microsoft.</span><span class="sxs-lookup"><span data-stu-id="aa236-108">[Periodic Table of the Elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is an open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="aa236-109">Erfahren Sie, wie Sie mithilfe einer **[Objekt](../../design/object-collection.md)** Auflistung ein Array von Objekten im 3D-Raum mit verschiedenen Oberflächentypen aufstellen.</span><span class="sxs-lookup"><span data-stu-id="aa236-109">Learn how to lay out an array of objects in 3D space with various surface types using an **[Object collection](../../design/object-collection.md)**.</span></span> <span data-ttu-id="aa236-110">Außerdem wird beschrieben, wie Sie Objekt übergreifende Objekte erstellen, die auf Standard Eingaben aus hololens reagieren.</span><span class="sxs-lookup"><span data-stu-id="aa236-110">Also learn how to create interactable objects that respond to standard inputs from HoloLens.</span></span> <span data-ttu-id="aa236-111">Sie können die Komponenten dieses Projekts verwenden, um Ihre eigene Benutzeroberflächen Funktion für gemischte Realität zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="aa236-111">You can use this project's components to create your own mixed reality app experience.</span></span>

![Period-Tabelle der Elements-App](images/640px-periodictable-hero.jpg)

## <a name="demo-video"></a><span data-ttu-id="aa236-113">Demovideo</span><span class="sxs-lookup"><span data-stu-id="aa236-113">Demo video</span></span> 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCF]

<span data-ttu-id="aa236-114">Aufgezeichnet mit hololens 2 mithilfe von Mixed Reality Capture</span><span class="sxs-lookup"><span data-stu-id="aa236-114">Recorded with HoloLens 2 using Mixed Reality Capture</span></span>

## <a name="about-the-app"></a><span data-ttu-id="aa236-115">Informationen zur APP</span><span class="sxs-lookup"><span data-stu-id="aa236-115">About the app</span></span>

<span data-ttu-id="aa236-116">Eine periodische Tabelle der Elemente visualisiert die chemischen Elemente und ihre Eigenschaften in einem 3D-Raum.</span><span class="sxs-lookup"><span data-stu-id="aa236-116">Periodic Table of the Elements visualizes the chemical elements and each of their properties in a 3D space.</span></span> <span data-ttu-id="aa236-117">Es umfasst die grundlegenden Interaktionen von hololens, wie z. b. "Blick" und "Air Tap</span><span class="sxs-lookup"><span data-stu-id="aa236-117">It incorporates the basic interactions of HoloLens such as gaze and air tap.</span></span> <span data-ttu-id="aa236-118">Benutzer können sich über die Elemente mit animierten 3D-Modellen informieren.</span><span class="sxs-lookup"><span data-stu-id="aa236-118">Users can learn about the elements with animated 3D models.</span></span> <span data-ttu-id="aa236-119">Sie können die Elektronen Shell eines Elements und den Kern, der aus den Protonen und den neutralen besteht, visuell verstehen.</span><span class="sxs-lookup"><span data-stu-id="aa236-119">They can visually understand an element's electron shell and its nucleus - which is composed of protons and neutrons.</span></span>

## <a name="background"></a><span data-ttu-id="aa236-120">Hintergrund</span><span class="sxs-lookup"><span data-stu-id="aa236-120">Background</span></span>

<span data-ttu-id="aa236-121">Nachdem ich die ersten hololens erlebt habe, wusste ich, dass ich mit einer regelmäßigen Tabellen-app in gemischter Realität experimentieren wollte.</span><span class="sxs-lookup"><span data-stu-id="aa236-121">After I first experienced HoloLens, I knew I wanted to experiment with a periodic table app in mixed reality.</span></span> <span data-ttu-id="aa236-122">Da jedes Element viele Datenpunkte enthält, die mit Text angezeigt werden, dachte ich, dass es sich um die Untersuchung der typografischen Komposition in einem 3D-Raum handelt.</span><span class="sxs-lookup"><span data-stu-id="aa236-122">Since each element has many data points that are displayed with text, I thought it would be great subject matter for exploring typographic composition in a 3D space.</span></span> <span data-ttu-id="aa236-123">Den Benutzern die Möglichkeit zu geben, das Elektronen Modell des Elements visuell darzustellen, war ein weiterer interessanter Bestandteil dieses Projekts.</span><span class="sxs-lookup"><span data-stu-id="aa236-123">Giving users the chance to visualize the element's electron model was another interesting part of this project.</span></span>

## <a name="design"></a><span data-ttu-id="aa236-124">Entwurf</span><span class="sxs-lookup"><span data-stu-id="aa236-124">Design</span></span>

<span data-ttu-id="aa236-125">In der Standardansicht der periodischen Tabelle habe ich dreidimensionale Felder vorgestellt, die das Elektronen Modell der einzelnen Elemente enthalten würden.</span><span class="sxs-lookup"><span data-stu-id="aa236-125">For the default view of the periodic table, I imagined three-dimensional boxes that would contain the electron model of each element.</span></span> <span data-ttu-id="aa236-126">Die Oberfläche jedes Felds wäre über scheinend, sodass der Benutzer einen groben Überblick über das Volume des Elements erhalten könnte.</span><span class="sxs-lookup"><span data-stu-id="aa236-126">The surface of each box would be translucent so that the user could get a rough idea of the element's volume.</span></span> <span data-ttu-id="aa236-127">Mit Blick und Luft tippen könnte der Benutzer eine ausführliche Ansicht der einzelnen Elemente öffnen.</span><span class="sxs-lookup"><span data-stu-id="aa236-127">With gaze and air tap, the user could open up a detailed view of each element.</span></span> <span data-ttu-id="aa236-128">Um den Übergang zwischen der Tabellenansicht und der Detailansicht reibungslos und natürlich zu gestalten, habe ich die physische Interaktion eines Box-Öffnens in der Praxis ähnlich gestaltet.</span><span class="sxs-lookup"><span data-stu-id="aa236-128">To make the transition between table view and detail view smooth and natural, I made it similar to the physical interaction of a box opening in real life.</span></span>

<span data-ttu-id="aa236-129">![Entwurfsskizze](images/640px-sketch20170406.jpg)</span><span class="sxs-lookup"><span data-stu-id="aa236-129">![Design sketch](images/640px-sketch20170406.jpg)</span></span><br>
<span data-ttu-id="aa236-130">*Entwurfsskizzen*</span><span class="sxs-lookup"><span data-stu-id="aa236-130">*Design sketches*</span></span>

<span data-ttu-id="aa236-131">In der Detailansicht wollte ich die Informationen jedes Elements mit schön gerendertem Text im 3D-Raum visualisieren.</span><span class="sxs-lookup"><span data-stu-id="aa236-131">In detail view, I wanted to visualize the information of each element with beautifully rendered text in 3D space.</span></span> <span data-ttu-id="aa236-132">Das animierte 3D-Elektronen Modell wird im mittleren Bereich angezeigt und kann aus unterschiedlichen Winkeln angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="aa236-132">The animated 3D electron model is displayed in the center area and can be viewed from different angles.</span></span>

![Interaktion](images/640px-periodictable-interaction.jpg)

<span data-ttu-id="aa236-134">![Ty](images/640px-periodictable-prototypes.jpg)</span><span class="sxs-lookup"><span data-stu-id="aa236-134">![Prototypes](images/640px-periodictable-prototypes.jpg)</span></span><br>
<span data-ttu-id="aa236-135">*Interaktions Prototypen*</span><span class="sxs-lookup"><span data-stu-id="aa236-135">*Interaction prototypes*</span></span>

<span data-ttu-id="aa236-136">Der Benutzer kann den Surface-Typ ändern, indem er auf die Schaltflächen am unteren Ende der Tabelle tippt. Sie können Zwischenebene, Zylinder, Kugel und Punkt umschalten.</span><span class="sxs-lookup"><span data-stu-id="aa236-136">The user can change the surface type by air tapping the buttons on the bottom of the table - they can switch between plane, cylinder, sphere, and scatter.</span></span>

## <a name="common-controls-and-patterns-used-in-this-app"></a><span data-ttu-id="aa236-137">In dieser APP verwendete allgemeine Steuerelemente und Muster</span><span class="sxs-lookup"><span data-stu-id="aa236-137">Common controls and patterns used in this app</span></span>

### <a name="interactable-object-button"></a><span data-ttu-id="aa236-138">Interactable-Objekt (Schaltfläche)</span><span class="sxs-lookup"><span data-stu-id="aa236-138">Interactable object (button)</span></span>

<span data-ttu-id="aa236-139">Das [interactable-Objekt](../../design/interactable-object.md) ist ein Objekt, das auf grundlegende hololens-Eingaben reagieren kann.</span><span class="sxs-lookup"><span data-stu-id="aa236-139">[Interactable object](../../design/interactable-object.md) is an object, which can respond to basic HoloLens inputs.</span></span> <span data-ttu-id="aa236-140">Sie wird als präfab/Skript bereitgestellt, das Sie problemlos auf jedes beliebige Objekt anwenden können.</span><span class="sxs-lookup"><span data-stu-id="aa236-140">It's provided as a prefab/script, which you can easily apply to any object.</span></span> <span data-ttu-id="aa236-141">Sie können z. b. einen Kaffeebecher in der Szene in der Szene zusammenstellen und auf Eingaben wie z. b. Blick, Luft tippen, Navigation und Manipulations Gesten reagieren.</span><span class="sxs-lookup"><span data-stu-id="aa236-141">For example, you can make a coffee cup in your scene interactable and respond to inputs such as gaze, air tap, navigation, and manipulation gestures.</span></span> [<span data-ttu-id="aa236-142">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="aa236-142">Learn more</span></span>](../../design/interactable-object.md)

![nteractable-Objekt](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a><span data-ttu-id="aa236-144">Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="aa236-144">Object collection</span></span>

<span data-ttu-id="aa236-145">Die [Objektsammlung](../../design/object-collection.md) ist ein Objekt, mit dem Sie mehrere Objekte in verschiedenen Formen anordnen können.</span><span class="sxs-lookup"><span data-stu-id="aa236-145">[Object collection](../../design/object-collection.md) is an object, which helps you lay out multiple objects in various shapes.</span></span> <span data-ttu-id="aa236-146">Es unterstützt Ebene, Zylinder, Kugel und Punkt.</span><span class="sxs-lookup"><span data-stu-id="aa236-146">It supports plane, cylinder, sphere, and scatter.</span></span> <span data-ttu-id="aa236-147">Sie können zusätzliche Eigenschaften wie RADIUS, Anzahl der Zeilen und den Abstand konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="aa236-147">You can configure additional properties such as radius, number of rows and the spacing.</span></span> [<span data-ttu-id="aa236-148">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="aa236-148">Learn more</span></span>](../../design/object-collection.md)

![Objektsammlung](images/640px-periodictable-collections.jpg)

## <a name="technical-details"></a><span data-ttu-id="aa236-150">Technische Details</span><span class="sxs-lookup"><span data-stu-id="aa236-150">Technical details</span></span>

<span data-ttu-id="aa236-151">Sie finden Skripts und Prefabs für die periodische Tabelle der Elements-App auf dem [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span><span class="sxs-lookup"><span data-stu-id="aa236-151">You can find scripts and prefabs for the Periodic Table of the Elements app on the [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span></span>

## <a name="porting-story-for-hololens-2"></a><span data-ttu-id="aa236-152">Portieren von Story für hololens 2</span><span class="sxs-lookup"><span data-stu-id="aa236-152">Porting story for HoloLens 2</span></span>

<span data-ttu-id="aa236-153">Lesen Sie den Artikel zum Aktualisieren der periodischen Tabelle der Elements-App mit den instanziellen Interaktionen von hololens 2.</span><span class="sxs-lookup"><span data-stu-id="aa236-153">Read the story on how Periodic Table of the Elements app was updated with HoloLens 2's instinctual interactions.</span></span>

[<span data-ttu-id="aa236-154">Periodensystem der Elemente 2.0</span><span class="sxs-lookup"><span data-stu-id="aa236-154">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)




## <a name="about-the-author"></a><span data-ttu-id="aa236-155">Informationen zum Autor</span><span class="sxs-lookup"><span data-stu-id="aa236-155">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="aa236-156"><b>Dong-Yoon-Park</b></span><span class="sxs-lookup"><span data-stu-id="aa236-156"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="aa236-157">UX-Designer @Microsoft</span><span class="sxs-lookup"><span data-stu-id="aa236-157">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="aa236-158">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="aa236-158">See also</span></span>

* <span data-ttu-id="aa236-159">[Hub für MRTK-Beispiele](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ExampleHub.html) - [(Aus dem Microsoft Store in HoloLens 2 herunterladen)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span><span class="sxs-lookup"><span data-stu-id="aa236-159">[MRTK Examples Hub](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ExampleHub.html) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span></span>
* <span data-ttu-id="aa236-160">[Oberflächen](sampleapp-surfaces.md) - [(Aus dem Microsoft Store in HoloLens 2 herunterladen)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span><span class="sxs-lookup"><span data-stu-id="aa236-160">[Surfaces](sampleapp-surfaces.md) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span></span>
* [<span data-ttu-id="aa236-161">Periodensystem der Elemente 2.0</span><span class="sxs-lookup"><span data-stu-id="aa236-161">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [<span data-ttu-id="aa236-162">Galaxy Explorer 2.0</span><span class="sxs-lookup"><span data-stu-id="aa236-162">Galaxy Explorer 2.0</span></span>](galaxy-explorer-update.md)