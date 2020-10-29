---
title: Periodensystem der Elemente
description: Die periodische Tabelle der Elemente ist eine Open-Source-Beispiel-App aus der Mixed Reality Design Labs von Microsoft, in der Sie erfahren, wie Sie mithilfe einer Objekt Auflistung ein Array von Objekten im 3D-Raum mit verschiedenen Oberflächentypen erstellen können.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Gemischte Windows-Realität, Entwurf, Beispiel-APP, Steuerelemente
ms.openlocfilehash: 2f7120aaf92a6e3d7b6ace301aae7392b67fa00b
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2020
ms.locfileid: "91690166"
---
# <a name="periodic-table-of-the-elements"></a><span data-ttu-id="c6d73-104">Periodensystem der Elemente</span><span class="sxs-lookup"><span data-stu-id="c6d73-104">Periodic Table of the Elements</span></span>

>[!NOTE]
><span data-ttu-id="c6d73-105">In diesem Artikel wird ein exploratives Beispiel erläutert, das wir in den [Entwurfs Labors für gemischte Realität](https://github.com/Microsoft/MRDesignLabs_Unity)erstellt haben, einem Ort, an dem wir unsere Erkenntnisse und Vorschläge für die Entwicklung gemischter Reality-apps teilen.</span><span class="sxs-lookup"><span data-stu-id="c6d73-105">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="c6d73-106">Unsere Entwurfs bezogenen Artikel und Code werden sich weiterentwickeln, wenn wir neue Ermittlungen durchführen.</span><span class="sxs-lookup"><span data-stu-id="c6d73-106">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="c6d73-107">[Die periodische Tabelle der Elemente](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) ist eine Open-Source-Beispiel-App aus den Mixed Reality-Entwurfs Labs von Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c6d73-107">[Periodic Table of the Elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is a open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="c6d73-108">Mit diesem Projekt können Sie erfahren, wie Sie ein Array von Objekten im 3D-Raum mit verschiedenen Oberflächentypen mithilfe einer **[Objekt](../../design/object-collection.md)** Auflistung aufstellen.</span><span class="sxs-lookup"><span data-stu-id="c6d73-108">With this project, you can learn how to lay out an array of objects in 3D space with various surface types using an **[Object collection](../../design/object-collection.md)** .</span></span> <span data-ttu-id="c6d73-109">Außerdem wird beschrieben, wie Sie Objekt übergreifende Objekte erstellen, die auf Standard Eingaben aus hololens reagieren.</span><span class="sxs-lookup"><span data-stu-id="c6d73-109">Also learn how to create interactable objects that respond to standard inputs from HoloLens.</span></span> <span data-ttu-id="c6d73-110">Sie können die Komponenten dieses Projekts verwenden, um Ihre eigene Benutzeroberflächen Funktion für gemischte Realität zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="c6d73-110">You can use this project's components to create your own mixed reality app experience.</span></span>

![Period-Tabelle der Elements-App](images/640px-periodictable-hero.jpg)

## <a name="about-the-app"></a><span data-ttu-id="c6d73-112">Informationen zur APP</span><span class="sxs-lookup"><span data-stu-id="c6d73-112">About the app</span></span>

<span data-ttu-id="c6d73-113">Eine periodische Tabelle der Elemente visualisiert die chemischen Elemente und ihre Eigenschaften in einem 3D-Raum.</span><span class="sxs-lookup"><span data-stu-id="c6d73-113">Periodic Table of the Elements visualizes the chemical elements and each of their properties in a 3D space.</span></span> <span data-ttu-id="c6d73-114">Es umfasst die grundlegenden Interaktionen von hololens, wie z. b. "Blick" und "Air Tap</span><span class="sxs-lookup"><span data-stu-id="c6d73-114">It incorporates the basic interactions of HoloLens such as gaze and air tap.</span></span> <span data-ttu-id="c6d73-115">Benutzer können sich über die Elemente mit animierten 3D-Modellen informieren.</span><span class="sxs-lookup"><span data-stu-id="c6d73-115">Users can learn about the elements with animated 3D models.</span></span> <span data-ttu-id="c6d73-116">Sie können die Elektronen Shell eines Elements und den Kern, der aus den Protonen und den neutralen besteht, visuell verstehen.</span><span class="sxs-lookup"><span data-stu-id="c6d73-116">They can visually understand an element's electron shell and its nucleus - which is composed of protons and neutrons.</span></span>

## <a name="background"></a><span data-ttu-id="c6d73-117">Hintergrund</span><span class="sxs-lookup"><span data-stu-id="c6d73-117">Background</span></span>

<span data-ttu-id="c6d73-118">Nachdem ich die ersten hololens erlebt habe, war eine regelmäßige Tabellen-App eine Idee, mit der ich wusste, dass ich in gemischter Realität experimentieren wollte.</span><span class="sxs-lookup"><span data-stu-id="c6d73-118">After I first experienced HoloLens, a periodic table app was an idea I knew that I wanted to experiment with in mixed reality.</span></span> <span data-ttu-id="c6d73-119">Da jedes Element viele Datenpunkte enthält, die mit Text angezeigt werden, dachte ich, dass es sich um die Untersuchung der typografischen Komposition in einem 3D-Raum handelt.</span><span class="sxs-lookup"><span data-stu-id="c6d73-119">Since each element has many data points that are displayed with text, I thought it would be great subject matter for exploring typographic composition in a 3D space.</span></span> <span data-ttu-id="c6d73-120">Es war ein weiterer interessanter Bestandteil dieses Projekts, das-Elektronen Modell des Elements visuell darzustellen.</span><span class="sxs-lookup"><span data-stu-id="c6d73-120">Being able to visualize the element's electron model was another interesting part of this project.</span></span>

## <a name="design"></a><span data-ttu-id="c6d73-121">Entwurf</span><span class="sxs-lookup"><span data-stu-id="c6d73-121">Design</span></span>

<span data-ttu-id="c6d73-122">In der Standardansicht der periodischen Tabelle habe ich dreidimensionale Felder vorgestellt, die das Elektronen Modell der einzelnen Elemente enthalten würden.</span><span class="sxs-lookup"><span data-stu-id="c6d73-122">For the default view of the periodic table, I imagined three-dimensional boxes that would contain the electron model of each element.</span></span> <span data-ttu-id="c6d73-123">Die Oberfläche jedes Felds wäre über scheinend, sodass der Benutzer einen groben Überblick über das Volume des Elements erhalten könnte.</span><span class="sxs-lookup"><span data-stu-id="c6d73-123">The surface of each box would be translucent so that the user could get a rough idea of the element's volume.</span></span> <span data-ttu-id="c6d73-124">Mit Blick und Luft tippen könnte der Benutzer eine ausführliche Ansicht der einzelnen Elemente öffnen.</span><span class="sxs-lookup"><span data-stu-id="c6d73-124">With gaze and air tap, the user could open up a detailed view of each element.</span></span> <span data-ttu-id="c6d73-125">Um den Übergang zwischen der Tabellenansicht und der Detailansicht reibungslos und natürlich zu gestalten, habe ich die physische Interaktion eines Box-Öffnens in der Praxis ähnlich gestaltet.</span><span class="sxs-lookup"><span data-stu-id="c6d73-125">To make the transition between table view and detail view smooth and natural, I made it similar to the physical interaction of a box opening in real life.</span></span>

<span data-ttu-id="c6d73-126">![Entwurfsskizze](images/640px-sketch20170406.jpg)</span><span class="sxs-lookup"><span data-stu-id="c6d73-126">![Design sketch](images/640px-sketch20170406.jpg)</span></span><br>
<span data-ttu-id="c6d73-127">*Entwurfsskizzen*</span><span class="sxs-lookup"><span data-stu-id="c6d73-127">*Design sketches*</span></span>

<span data-ttu-id="c6d73-128">In der Detailansicht wollte ich die Informationen jedes Elements mit schön gerendertem Text im 3D-Raum visualisieren.</span><span class="sxs-lookup"><span data-stu-id="c6d73-128">In detail view, I wanted to visualize the information of each element with beautifully rendered text in 3D space.</span></span> <span data-ttu-id="c6d73-129">Das animierte 3D-Elektronen Modell wird im mittleren Bereich angezeigt und kann aus unterschiedlichen Winkeln angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="c6d73-129">The animated 3D electron model is displayed in the center area and can be viewed from different angles.</span></span>

![Interaktion](images/640px-periodictable-interaction.jpg)

<span data-ttu-id="c6d73-131">![Ty](images/640px-periodictable-prototypes.jpg)</span><span class="sxs-lookup"><span data-stu-id="c6d73-131">![Prototypes](images/640px-periodictable-prototypes.jpg)</span></span><br>
<span data-ttu-id="c6d73-132">*Interaktions Prototypen*</span><span class="sxs-lookup"><span data-stu-id="c6d73-132">*Interaction prototypes*</span></span>

<span data-ttu-id="c6d73-133">Der Benutzer kann den Surface-Typ ändern, indem er auf die Schaltflächen am unteren Ende der Tabelle tippt. er kann Zwischenebene, Zylinder, Kugel und Punkt wechseln.</span><span class="sxs-lookup"><span data-stu-id="c6d73-133">The user can change the surface type by air tapping the buttons on the bottom of the table - they can switch between plane, cylinder, sphere and scatter.</span></span>

## <a name="common-controls-and-patterns-used-in-this-app"></a><span data-ttu-id="c6d73-134">In dieser APP verwendete allgemeine Steuerelemente und Muster</span><span class="sxs-lookup"><span data-stu-id="c6d73-134">Common controls and patterns used in this app</span></span>

### <a name="interactable-object-button"></a><span data-ttu-id="c6d73-135">Interactable-Objekt (Schaltfläche)</span><span class="sxs-lookup"><span data-stu-id="c6d73-135">Interactable object (button)</span></span>

<span data-ttu-id="c6d73-136">Das [interactable-Objekt](../../design/interactable-object.md) ist ein Objekt, das auf grundlegende hololens-Eingaben reagieren kann.</span><span class="sxs-lookup"><span data-stu-id="c6d73-136">[Interactable object](../../design/interactable-object.md) is an object which can respond to basic HoloLens inputs.</span></span> <span data-ttu-id="c6d73-137">Sie wird als präfab/-Skript bereitgestellt, das Sie problemlos auf jedes beliebige Objekt anwenden können.</span><span class="sxs-lookup"><span data-stu-id="c6d73-137">It is provided as a prefab/script which you can easily apply to any object.</span></span> <span data-ttu-id="c6d73-138">Beispielsweise können Sie einen Kaffeebecher in der Szene in der Szene zusammenstellen und auf Eingaben wie z. b. Blick, Luft tippen, Navigation und Manipulations Gesten reagieren.</span><span class="sxs-lookup"><span data-stu-id="c6d73-138">For example, you can make a coffee cup in your scene interactable and respond to inputs such as gaze, air tap, navigation and manipulation gestures.</span></span> [<span data-ttu-id="c6d73-139">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="c6d73-139">Learn more</span></span>](../../design/interactable-object.md)

![nteractable-Objekt](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a><span data-ttu-id="c6d73-141">Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="c6d73-141">Object collection</span></span>

<span data-ttu-id="c6d73-142">Die [Objektsammlung](../../design/object-collection.md) ist ein Objekt, mit dem Sie mehrere Objekte in verschiedenen Formen anordnen können.</span><span class="sxs-lookup"><span data-stu-id="c6d73-142">[Object collection](../../design/object-collection.md) is an object which helps you lay out multiple objects in various shapes.</span></span> <span data-ttu-id="c6d73-143">Es unterstützt die Ebenen, Zylinder, Kugel und Punkt.</span><span class="sxs-lookup"><span data-stu-id="c6d73-143">It supports plane, cylinder, sphere and scatter.</span></span> <span data-ttu-id="c6d73-144">Sie können zusätzliche Eigenschaften wie RADIUS, Anzahl der Zeilen und den Abstand konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="c6d73-144">You can configure additional properties such as radius, number of rows and the spacing.</span></span> [<span data-ttu-id="c6d73-145">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="c6d73-145">Learn more</span></span>](../../design/object-collection.md)

![Objektsammlung](images/640px-periodictable-collections.jpg)

### <a name="fitbox"></a><span data-ttu-id="c6d73-147">Fitbox</span><span class="sxs-lookup"><span data-stu-id="c6d73-147">Fitbox</span></span>

<span data-ttu-id="c6d73-148">In der Standardeinstellung werden holograms an dem Speicherort abgelegt, an dem der Benutzer die Anwendung startet.</span><span class="sxs-lookup"><span data-stu-id="c6d73-148">By default, holograms will be placed in the location where the user is gazing at the moment the application is launched.</span></span> <span data-ttu-id="c6d73-149">Dies führt manchmal zu unerwünschten Ergebnissen, z. b. holograms, die hinter einer Wand oder in der Mitte einer Tabelle abgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="c6d73-149">This sometimes leads to unwanted result such as holograms being placed behind a wall or in the middle of a table.</span></span> <span data-ttu-id="c6d73-150">Eine fitbox-Funktion ermöglicht es einem Benutzer, die Position zu ermitteln, an der das – Hologramm platziert wird.</span><span class="sxs-lookup"><span data-stu-id="c6d73-150">A fitbox allows a user to use gaze to determine the location where the hologram will be placed.</span></span> <span data-ttu-id="c6d73-151">Sie wird mit einer einfachen PNG-Bildtextur erstellt, die problemlos mit ihren eigenen Bildern oder 3D-Objekten angepasst werden kann.</span><span class="sxs-lookup"><span data-stu-id="c6d73-151">It is made with a simple PNG image texture which can be easily customized with your own images or 3D objects.</span></span>

![Fitbox](../../design/images/450px-periodictable-fitbox.jpg)

## <a name="technical-details"></a><span data-ttu-id="c6d73-153">Technische Details</span><span class="sxs-lookup"><span data-stu-id="c6d73-153">Technical details</span></span>

<span data-ttu-id="c6d73-154">Sie finden Skripts und Prefabs für die periodische Tabelle der Elements-App auf dem [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span><span class="sxs-lookup"><span data-stu-id="c6d73-154">You can find scripts and prefabs for the Periodic Table of the Elements app on the [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span></span>

## <a name="application-examples"></a><span data-ttu-id="c6d73-155">Anwendungsbeispiele</span><span class="sxs-lookup"><span data-stu-id="c6d73-155">Application examples</span></span>

<span data-ttu-id="c6d73-156">Im folgenden finden Sie einige Ideen für das, was Sie erstellen können, indem Sie die Komponenten in diesem Projekt nutzen.</span><span class="sxs-lookup"><span data-stu-id="c6d73-156">Here are some ideas for what you could create by leveraging the components in this project.</span></span>

### <a name="stock-data-visualization-app"></a><span data-ttu-id="c6d73-157">Daten Visualisierungs-App für Aktien</span><span class="sxs-lookup"><span data-stu-id="c6d73-157">Stock data visualization app</span></span>

<span data-ttu-id="c6d73-158">Wenn Sie die gleichen Steuerelemente und das Interaktionsmodell wie die periodische Tabelle des Elements Sample verwenden, können Sie eine APP erstellen, die die Daten von Aktienmärkten visualisiert.</span><span class="sxs-lookup"><span data-stu-id="c6d73-158">Using the same controls and interaction model as the Periodic Table of the Elements sample, you could build an app which visualizes stock market data.</span></span> <span data-ttu-id="c6d73-159">In diesem Beispiel wird das Objekt Auflistungs Steuerelement verwendet, um Aktiendaten in einer kugelförmigen Form anzuordnen.</span><span class="sxs-lookup"><span data-stu-id="c6d73-159">This example uses the Object collection control to lay out stock data in a spherical shape.</span></span> <span data-ttu-id="c6d73-160">Sie können sich eine Detailansicht vorstellen, in der zusätzliche Informationen zu den einzelnen Aktien auf interessante Weise angezeigt werden können.</span><span class="sxs-lookup"><span data-stu-id="c6d73-160">You can imagine a detail view where additional information about each stock could be displayed in an interesting way.</span></span>

![Anwendungsbeispiel: Finance (1 von 3)](images/640px-periodictable-applicationexamples-finance1.jpg)

![Anwendungsbeispiel: Finance (2 von 3)](images/640px-periodictable-applicationexamples-finance2.jpg)

<span data-ttu-id="c6d73-163">![Anwendungsbeispiel: Finance (3 von 3)](images/640px-periodictable-applicationexamples-finance3.jpg)</span><span class="sxs-lookup"><span data-stu-id="c6d73-163">![Application example: Finance (3 of 3)](images/640px-periodictable-applicationexamples-finance3.jpg)</span></span><br>
<span data-ttu-id="c6d73-164">*Ein Beispiel dafür, wie die Objekt Auflistung, die in der periodischen Tabelle der Beispiel-App für Elemente verwendet wird, in einer Finance-App verwendet werden kann*</span><span class="sxs-lookup"><span data-stu-id="c6d73-164">*An example of how the Object collection used in the Periodic Table of the Elements sample app could be used in a finance app*</span></span>

### <a name="sports-app"></a><span data-ttu-id="c6d73-165">Sport-App</span><span class="sxs-lookup"><span data-stu-id="c6d73-165">Sports app</span></span>

<span data-ttu-id="c6d73-166">Dies ist ein Beispiel für die Visualisierung von Sportdaten mithilfe der Objekt Auflistung und anderer Komponenten aus der periodischen Tabelle der Elements-Beispiel-app.</span><span class="sxs-lookup"><span data-stu-id="c6d73-166">This is an example of visualizing sports data using Object collection and other components from the Periodic Table of the Elements sample app.</span></span>

![Anwendungsbeispiel: Sport (1 von 3)](images/640px-periodictable-applicationexamples-sports0.jpg)

![Anwendungsbeispiel: Sport (2 von 3)](images/640px-periodictable-applicationexamples-sports1.jpg)

<span data-ttu-id="c6d73-169">![Anwendungsbeispiel: Sport (3 von 3)](images/640px-periodictable-applicationexamples-sports3.jpg)</span><span class="sxs-lookup"><span data-stu-id="c6d73-169">![Application example: Sports (3 of 3)](images/640px-periodictable-applicationexamples-sports3.jpg)</span></span><br>
<span data-ttu-id="c6d73-170">*Ein Beispiel dafür, wie die Objekt Auflistung, die in der periodischen Tabelle des Elements Sample appused verwendet wird, in einer Sport-App verwendet werden kann.*</span><span class="sxs-lookup"><span data-stu-id="c6d73-170">*An example of how the Object collection used in the Periodic Table of the Elements sample appcould be used in a sports app*</span></span>

## <a name="about-the-author"></a><span data-ttu-id="c6d73-171">Zum Autor</span><span class="sxs-lookup"><span data-stu-id="c6d73-171">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="c6d73-172"><b>Dong-Yoon-Park</b></span><span class="sxs-lookup"><span data-stu-id="c6d73-172"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="c6d73-173">UX-Designer @Microsoft</span><span class="sxs-lookup"><span data-stu-id="c6d73-173">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="c6d73-174">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="c6d73-174">See also</span></span>

* [<span data-ttu-id="c6d73-175">Interaktionsfähiges Objekt</span><span class="sxs-lookup"><span data-stu-id="c6d73-175">Interactable object</span></span>](../../design/interactable-object.md)
* [<span data-ttu-id="c6d73-176">Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="c6d73-176">Object collection</span></span>](../../design/object-collection.md)
