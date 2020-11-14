---
title: Periodensystem der Elemente
description: Die periodische Tabelle der Elemente ist eine Open-Source-Beispiel-App aus der Mixed Reality Design Labs von Microsoft, in der Sie erfahren, wie Sie mithilfe einer Objekt Auflistung ein Array von Objekten im 3D-Raum mit verschiedenen Oberflächentypen erstellen können.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Gemischte Windows-Realität, Entwurf, Beispiel-APP, Steuerelemente
ms.openlocfilehash: 82ffa19b27c1d2687b67df659cb3bb50544748fc
ms.sourcegitcommit: 8a80613f025b05a83393845d4af4da26a7d3ea9c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2020
ms.locfileid: "94573264"
---
# <a name="periodic-table-of-the-elements"></a><span data-ttu-id="9c1a7-104">Periodensystem der Elemente</span><span class="sxs-lookup"><span data-stu-id="9c1a7-104">Periodic Table of the Elements</span></span>

>[!NOTE]
><span data-ttu-id="9c1a7-105">In diesem Artikel wird ein exploratives Beispiel erläutert, das wir in den [Entwurfs Labors für gemischte Realität](https://github.com/Microsoft/MRDesignLabs_Unity)erstellt haben, einem Ort, an dem wir unsere Erkenntnisse und Vorschläge für die Entwicklung gemischter Reality-apps teilen.</span><span class="sxs-lookup"><span data-stu-id="9c1a7-105">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="9c1a7-106">Unsere Entwurfs bezogenen Artikel und Code werden sich weiterentwickeln, wenn wir neue Ermittlungen durchführen.</span><span class="sxs-lookup"><span data-stu-id="9c1a7-106">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="9c1a7-107">[Die periodische Tabelle der Elemente](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) ist eine Open-Source-Beispiel-App aus den Mixed Reality-Entwurfs Labs von Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9c1a7-107">[Periodic Table of the Elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is a open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="9c1a7-108">Mit diesem Projekt können Sie erfahren, wie Sie ein Array von Objekten im 3D-Raum mit verschiedenen Oberflächentypen mithilfe einer **[Objekt](../../design/object-collection.md)** Auflistung aufstellen.</span><span class="sxs-lookup"><span data-stu-id="9c1a7-108">With this project, you can learn how to lay out an array of objects in 3D space with various surface types using an **[Object collection](../../design/object-collection.md)**.</span></span> <span data-ttu-id="9c1a7-109">Außerdem wird beschrieben, wie Sie Objekt übergreifende Objekte erstellen, die auf Standard Eingaben aus hololens reagieren.</span><span class="sxs-lookup"><span data-stu-id="9c1a7-109">Also learn how to create interactable objects that respond to standard inputs from HoloLens.</span></span> <span data-ttu-id="9c1a7-110">Sie können die Komponenten dieses Projekts verwenden, um Ihre eigene Benutzeroberflächen Funktion für gemischte Realität zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="9c1a7-110">You can use this project's components to create your own mixed reality app experience.</span></span>

![Period-Tabelle der Elements-App](images/640px-periodictable-hero.jpg)

## <a name="demo-video"></a><span data-ttu-id="9c1a7-112">Demovideo</span><span class="sxs-lookup"><span data-stu-id="9c1a7-112">Demo video</span></span> 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCF]

<span data-ttu-id="9c1a7-113">Aufgezeichnet mit hololens 2 mithilfe von Mixed Reality Capture</span><span class="sxs-lookup"><span data-stu-id="9c1a7-113">Recorded with HoloLens 2 using Mixed Reality Capture</span></span>

## <a name="about-the-app"></a><span data-ttu-id="9c1a7-114">Informationen zur APP</span><span class="sxs-lookup"><span data-stu-id="9c1a7-114">About the app</span></span>

<span data-ttu-id="9c1a7-115">Eine periodische Tabelle der Elemente visualisiert die chemischen Elemente und ihre Eigenschaften in einem 3D-Raum.</span><span class="sxs-lookup"><span data-stu-id="9c1a7-115">Periodic Table of the Elements visualizes the chemical elements and each of their properties in a 3D space.</span></span> <span data-ttu-id="9c1a7-116">Es umfasst die grundlegenden Interaktionen von hololens, wie z. b. "Blick" und "Air Tap</span><span class="sxs-lookup"><span data-stu-id="9c1a7-116">It incorporates the basic interactions of HoloLens such as gaze and air tap.</span></span> <span data-ttu-id="9c1a7-117">Benutzer können sich über die Elemente mit animierten 3D-Modellen informieren.</span><span class="sxs-lookup"><span data-stu-id="9c1a7-117">Users can learn about the elements with animated 3D models.</span></span> <span data-ttu-id="9c1a7-118">Sie können die Elektronen Shell eines Elements und den Kern, der aus den Protonen und den neutralen besteht, visuell verstehen.</span><span class="sxs-lookup"><span data-stu-id="9c1a7-118">They can visually understand an element's electron shell and its nucleus - which is composed of protons and neutrons.</span></span>

## <a name="background"></a><span data-ttu-id="9c1a7-119">Hintergrund</span><span class="sxs-lookup"><span data-stu-id="9c1a7-119">Background</span></span>

<span data-ttu-id="9c1a7-120">Nachdem ich die ersten hololens erlebt habe, war eine regelmäßige Tabellen-App eine Idee, mit der ich wusste, dass ich in gemischter Realität experimentieren wollte.</span><span class="sxs-lookup"><span data-stu-id="9c1a7-120">After I first experienced HoloLens, a periodic table app was an idea I knew that I wanted to experiment with in mixed reality.</span></span> <span data-ttu-id="9c1a7-121">Da jedes Element viele Datenpunkte enthält, die mit Text angezeigt werden, dachte ich, dass es sich um die Untersuchung der typografischen Komposition in einem 3D-Raum handelt.</span><span class="sxs-lookup"><span data-stu-id="9c1a7-121">Since each element has many data points that are displayed with text, I thought it would be great subject matter for exploring typographic composition in a 3D space.</span></span> <span data-ttu-id="9c1a7-122">Es war ein weiterer interessanter Bestandteil dieses Projekts, das-Elektronen Modell des Elements visuell darzustellen.</span><span class="sxs-lookup"><span data-stu-id="9c1a7-122">Being able to visualize the element's electron model was another interesting part of this project.</span></span>

## <a name="design"></a><span data-ttu-id="9c1a7-123">Entwurf</span><span class="sxs-lookup"><span data-stu-id="9c1a7-123">Design</span></span>

<span data-ttu-id="9c1a7-124">In der Standardansicht der periodischen Tabelle habe ich dreidimensionale Felder vorgestellt, die das Elektronen Modell der einzelnen Elemente enthalten würden.</span><span class="sxs-lookup"><span data-stu-id="9c1a7-124">For the default view of the periodic table, I imagined three-dimensional boxes that would contain the electron model of each element.</span></span> <span data-ttu-id="9c1a7-125">Die Oberfläche jedes Felds wäre über scheinend, sodass der Benutzer einen groben Überblick über das Volume des Elements erhalten könnte.</span><span class="sxs-lookup"><span data-stu-id="9c1a7-125">The surface of each box would be translucent so that the user could get a rough idea of the element's volume.</span></span> <span data-ttu-id="9c1a7-126">Mit Blick und Luft tippen könnte der Benutzer eine ausführliche Ansicht der einzelnen Elemente öffnen.</span><span class="sxs-lookup"><span data-stu-id="9c1a7-126">With gaze and air tap, the user could open up a detailed view of each element.</span></span> <span data-ttu-id="9c1a7-127">Um den Übergang zwischen der Tabellenansicht und der Detailansicht reibungslos und natürlich zu gestalten, habe ich die physische Interaktion eines Box-Öffnens in der Praxis ähnlich gestaltet.</span><span class="sxs-lookup"><span data-stu-id="9c1a7-127">To make the transition between table view and detail view smooth and natural, I made it similar to the physical interaction of a box opening in real life.</span></span>

<span data-ttu-id="9c1a7-128">![Entwurfsskizze](images/640px-sketch20170406.jpg)</span><span class="sxs-lookup"><span data-stu-id="9c1a7-128">![Design sketch](images/640px-sketch20170406.jpg)</span></span><br>
<span data-ttu-id="9c1a7-129">*Entwurfsskizzen*</span><span class="sxs-lookup"><span data-stu-id="9c1a7-129">*Design sketches*</span></span>

<span data-ttu-id="9c1a7-130">In der Detailansicht wollte ich die Informationen jedes Elements mit schön gerendertem Text im 3D-Raum visualisieren.</span><span class="sxs-lookup"><span data-stu-id="9c1a7-130">In detail view, I wanted to visualize the information of each element with beautifully rendered text in 3D space.</span></span> <span data-ttu-id="9c1a7-131">Das animierte 3D-Elektronen Modell wird im mittleren Bereich angezeigt und kann aus unterschiedlichen Winkeln angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="9c1a7-131">The animated 3D electron model is displayed in the center area and can be viewed from different angles.</span></span>

![Interaktion](images/640px-periodictable-interaction.jpg)

<span data-ttu-id="9c1a7-133">![Ty](images/640px-periodictable-prototypes.jpg)</span><span class="sxs-lookup"><span data-stu-id="9c1a7-133">![Prototypes](images/640px-periodictable-prototypes.jpg)</span></span><br>
<span data-ttu-id="9c1a7-134">*Interaktions Prototypen*</span><span class="sxs-lookup"><span data-stu-id="9c1a7-134">*Interaction prototypes*</span></span>

<span data-ttu-id="9c1a7-135">Der Benutzer kann den Surface-Typ ändern, indem er auf die Schaltflächen am unteren Ende der Tabelle tippt. er kann Zwischenebene, Zylinder, Kugel und Punkt wechseln.</span><span class="sxs-lookup"><span data-stu-id="9c1a7-135">The user can change the surface type by air tapping the buttons on the bottom of the table - they can switch between plane, cylinder, sphere and scatter.</span></span>

## <a name="common-controls-and-patterns-used-in-this-app"></a><span data-ttu-id="9c1a7-136">In dieser APP verwendete allgemeine Steuerelemente und Muster</span><span class="sxs-lookup"><span data-stu-id="9c1a7-136">Common controls and patterns used in this app</span></span>

### <a name="interactable-object-button"></a><span data-ttu-id="9c1a7-137">Interactable-Objekt (Schaltfläche)</span><span class="sxs-lookup"><span data-stu-id="9c1a7-137">Interactable object (button)</span></span>

<span data-ttu-id="9c1a7-138">Das [interactable-Objekt](../../design/interactable-object.md) ist ein Objekt, das auf grundlegende hololens-Eingaben reagieren kann.</span><span class="sxs-lookup"><span data-stu-id="9c1a7-138">[Interactable object](../../design/interactable-object.md) is an object which can respond to basic HoloLens inputs.</span></span> <span data-ttu-id="9c1a7-139">Sie wird als präfab/-Skript bereitgestellt, das Sie problemlos auf jedes beliebige Objekt anwenden können.</span><span class="sxs-lookup"><span data-stu-id="9c1a7-139">It is provided as a prefab/script which you can easily apply to any object.</span></span> <span data-ttu-id="9c1a7-140">Beispielsweise können Sie einen Kaffeebecher in der Szene in der Szene zusammenstellen und auf Eingaben wie z. b. Blick, Luft tippen, Navigation und Manipulations Gesten reagieren.</span><span class="sxs-lookup"><span data-stu-id="9c1a7-140">For example, you can make a coffee cup in your scene interactable and respond to inputs such as gaze, air tap, navigation and manipulation gestures.</span></span> [<span data-ttu-id="9c1a7-141">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="9c1a7-141">Learn more</span></span>](../../design/interactable-object.md)

![nteractable-Objekt](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a><span data-ttu-id="9c1a7-143">Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="9c1a7-143">Object collection</span></span>

<span data-ttu-id="9c1a7-144">Die [Objektsammlung](../../design/object-collection.md) ist ein Objekt, mit dem Sie mehrere Objekte in verschiedenen Formen anordnen können.</span><span class="sxs-lookup"><span data-stu-id="9c1a7-144">[Object collection](../../design/object-collection.md) is an object which helps you lay out multiple objects in various shapes.</span></span> <span data-ttu-id="9c1a7-145">Es unterstützt die Ebenen, Zylinder, Kugel und Punkt.</span><span class="sxs-lookup"><span data-stu-id="9c1a7-145">It supports plane, cylinder, sphere and scatter.</span></span> <span data-ttu-id="9c1a7-146">Sie können zusätzliche Eigenschaften wie RADIUS, Anzahl der Zeilen und den Abstand konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="9c1a7-146">You can configure additional properties such as radius, number of rows and the spacing.</span></span> [<span data-ttu-id="9c1a7-147">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="9c1a7-147">Learn more</span></span>](../../design/object-collection.md)

![Objektsammlung](images/640px-periodictable-collections.jpg)

## <a name="technical-details"></a><span data-ttu-id="9c1a7-149">Technische Details</span><span class="sxs-lookup"><span data-stu-id="9c1a7-149">Technical details</span></span>

<span data-ttu-id="9c1a7-150">Sie finden Skripts und Prefabs für die periodische Tabelle der Elements-App auf dem [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span><span class="sxs-lookup"><span data-stu-id="9c1a7-150">You can find scripts and prefabs for the Periodic Table of the Elements app on the [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span></span>

## <a name="porting-story-for-hololens-2"></a><span data-ttu-id="9c1a7-151">Portieren von Story für hololens 2</span><span class="sxs-lookup"><span data-stu-id="9c1a7-151">Porting story for HoloLens 2</span></span>

<span data-ttu-id="9c1a7-152">Lesen Sie den Artikel zum Aktualisieren der periodischen Tabelle der Elements-App mit den instanziellen Interaktionen von hololens 2.</span><span class="sxs-lookup"><span data-stu-id="9c1a7-152">Read the story on how Periodic Table of the Elements app was updated with HoloLens 2's instinctual interactions.</span></span>

[<span data-ttu-id="9c1a7-153">Periodensystem der Elemente 2.0</span><span class="sxs-lookup"><span data-stu-id="9c1a7-153">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)




## <a name="about-the-author"></a><span data-ttu-id="9c1a7-154">Informationen zum Autor</span><span class="sxs-lookup"><span data-stu-id="9c1a7-154">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="9c1a7-155"><b>Dong-Yoon-Park</b></span><span class="sxs-lookup"><span data-stu-id="9c1a7-155"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="9c1a7-156">UX-Designer @Microsoft</span><span class="sxs-lookup"><span data-stu-id="9c1a7-156">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="9c1a7-157">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="9c1a7-157">See also</span></span>

* <span data-ttu-id="9c1a7-158">[Hub für MRTK-Beispiele](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ExampleHub.html) - [(Aus dem Microsoft Store in HoloLens 2 herunterladen)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span><span class="sxs-lookup"><span data-stu-id="9c1a7-158">[MRTK Examples Hub](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ExampleHub.html) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span></span>
* <span data-ttu-id="9c1a7-159">[Oberflächen](sampleapp-surfaces.md) - [(Aus dem Microsoft Store in HoloLens 2 herunterladen)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span><span class="sxs-lookup"><span data-stu-id="9c1a7-159">[Surfaces](sampleapp-surfaces.md) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span></span>
* [<span data-ttu-id="9c1a7-160">Periodensystem der Elemente 2.0</span><span class="sxs-lookup"><span data-stu-id="9c1a7-160">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [<span data-ttu-id="9c1a7-161">Galaxy Explorer 2.0</span><span class="sxs-lookup"><span data-stu-id="9c1a7-161">Galaxy Explorer 2.0</span></span>](galaxy-explorer-update.md)