---
title: Periodensystem der Elemente
description: Erfahren Sie, wie Sie ein Array von Objekten im 3D-Raum mit verschiedenen Oberflächentypen erstellen, indem Sie eine Objektsammlung mit dem Periodensystem der Beispiel-App Elements verwenden.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Design, Beispiel-App, Steuerelemente, MRTK, Mixed Reality Toolkit, Unity, Beispiel-Apps, Beispiel-Apps, Open Source, Microsoft Store, HoloLens, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: ed8c35fc6467322c25b92924b134f176fa4a9b47
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2021
ms.locfileid: "110743408"
---
# <a name="periodic-table-of-the-elements"></a><span data-ttu-id="d8964-104">Periodensystem der Elemente</span><span class="sxs-lookup"><span data-stu-id="d8964-104">Periodic Table of the Elements</span></span>

>[!NOTE]
><span data-ttu-id="d8964-105">In diesem Artikel wird ein exploratives Beispiel erläutert, das wir in den [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity)erstellt haben, einem Ort, an dem wir unsere Erfahrungen und Vorschläge für die Entwicklung von Mixed Reality-Apps teilen.</span><span class="sxs-lookup"><span data-stu-id="d8964-105">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="d8964-106">Unsere designbezogenen Artikel und der Code werden sich weiterentwickeln, wenn wir neue Erkenntnisse machen.</span><span class="sxs-lookup"><span data-stu-id="d8964-106">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="d8964-107">[Periodic Table of the Elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) ist eine Open Source-Beispiel-App aus den Mixed Reality Design Labs von Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d8964-107">[Periodic Table of the Elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is an open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="d8964-108">Erfahren Sie, wie Sie mithilfe einer Objektsammlung ein Array von Objekten im 3D-Raum mit verschiedenen **[Oberflächentypen erstellen.](../../design/object-collection.md)**</span><span class="sxs-lookup"><span data-stu-id="d8964-108">Learn how to lay out an array of objects in 3D space with various surface types using an **[Object collection](../../design/object-collection.md)**.</span></span> <span data-ttu-id="d8964-109">Außerdem erfahren Sie, wie Sie interaktionsfähige Objekte erstellen, die auf Standardeingaben von HoloLens reagieren.</span><span class="sxs-lookup"><span data-stu-id="d8964-109">Also learn how to create interactable objects that respond to standard inputs from HoloLens.</span></span> <span data-ttu-id="d8964-110">Sie können die Komponenten dieses Projekts verwenden, um Ihre eigene Mixed Reality-App-Erfahrung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="d8964-110">You can use this project's components to create your own mixed reality app experience.</span></span>

![Zeitraumtabelle der Elements-App](images/640px-periodictable-hero.jpg)

## <a name="demo-video"></a><span data-ttu-id="d8964-112">Demovideo</span><span class="sxs-lookup"><span data-stu-id="d8964-112">Demo video</span></span> 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCF]

<span data-ttu-id="d8964-113">Aufgezeichnet mit HoloLens 2 mit Mixed Reality-Aufnahme</span><span class="sxs-lookup"><span data-stu-id="d8964-113">Recorded with HoloLens 2 using Mixed Reality Capture</span></span>

## <a name="about-the-app"></a><span data-ttu-id="d8964-114">Informationen zur App</span><span class="sxs-lookup"><span data-stu-id="d8964-114">About the app</span></span>

<span data-ttu-id="d8964-115">Das Periodensystem der Elemente visualisiert die chemieischen Elemente und jede ihrer Eigenschaften in einem 3D-Raum.</span><span class="sxs-lookup"><span data-stu-id="d8964-115">Periodic Table of the Elements visualizes the chemical elements and each of their properties in a 3D space.</span></span> <span data-ttu-id="d8964-116">Es umfasst die grundlegenden Interaktionen von HoloLens, z. B. Anvogramm und Tippen in die Luft.</span><span class="sxs-lookup"><span data-stu-id="d8964-116">It incorporates the basic interactions of HoloLens such as gaze and air tap.</span></span> <span data-ttu-id="d8964-117">Benutzer können sich mit animierten 3D-Modellen über die Elemente informieren.</span><span class="sxs-lookup"><span data-stu-id="d8964-117">Users can learn about the elements with animated 3D models.</span></span> <span data-ttu-id="d8964-118">Sie können die Rastershell eines Elements und seine Hülle visuell verstehen, die aus Protonen und Protonen besteht.</span><span class="sxs-lookup"><span data-stu-id="d8964-118">They can visually understand an element's electron shell and its nucleus - which is composed of protons and neutrons.</span></span>

## <a name="background"></a><span data-ttu-id="d8964-119">Hintergrund</span><span class="sxs-lookup"><span data-stu-id="d8964-119">Background</span></span>

<span data-ttu-id="d8964-120">Nach der ersten Erfahrung mit HoloLens wusste ich, dass ich mit einer Periodentabellen-App in Mixed Reality experimentieren wollte.</span><span class="sxs-lookup"><span data-stu-id="d8964-120">After I first experienced HoloLens, I knew I wanted to experiment with a periodic table app in mixed reality.</span></span> <span data-ttu-id="d8964-121">Da jedes Element über viele Datenpunkte verfügt, die mit Text angezeigt werden, war ich der Meinung, dass es sich um ein hervorragendes Thema für die Untersuchung der typografischen Komposition in einem 3D-Raum handelt.</span><span class="sxs-lookup"><span data-stu-id="d8964-121">Since each element has many data points that are displayed with text, I thought it would be great subject matter for exploring typographic composition in a 3D space.</span></span> <span data-ttu-id="d8964-122">Es war ein weiterer interessanter Teil dieses Projekts, Benutzern die Möglichkeit zu geben, das Rastermodell des Elements zu visualisieren.</span><span class="sxs-lookup"><span data-stu-id="d8964-122">Giving users the chance to visualize the element's electron model was another interesting part of this project.</span></span>

## <a name="design"></a><span data-ttu-id="d8964-123">Entwurf</span><span class="sxs-lookup"><span data-stu-id="d8964-123">Design</span></span>

<span data-ttu-id="d8964-124">Für die Standardansicht des Periodensystems stellt ich mir dreidimensionale Felder vor, die das Rastermodell der einzelnen Elemente enthalten würden.</span><span class="sxs-lookup"><span data-stu-id="d8964-124">For the default view of the periodic table, I imagined three-dimensional boxes that would contain the electron model of each element.</span></span> <span data-ttu-id="d8964-125">Die Oberfläche jedes Felds wäre durchsichtig, sodass der Benutzer eine grobe Vorstellung vom Volume des Elements erhalten könnte.</span><span class="sxs-lookup"><span data-stu-id="d8964-125">The surface of each box would be translucent so that the user could get a rough idea of the element's volume.</span></span> <span data-ttu-id="d8964-126">Mit Anving und Tippen in die Luft kann der Benutzer eine detaillierte Ansicht der einzelnen Elemente öffnen.</span><span class="sxs-lookup"><span data-stu-id="d8964-126">With gaze and air tap, the user could open up a detailed view of each element.</span></span> <span data-ttu-id="d8964-127">Um den Übergang zwischen Tabellenansicht und Detailansicht reibungslos und natürlich zu machen, habe ich es der physischen Interaktion eines Felds ähnlich gemacht, das sich in der Realen öffnet.</span><span class="sxs-lookup"><span data-stu-id="d8964-127">To make the transition between table view and detail view smooth and natural, I made it similar to the physical interaction of a box opening in real life.</span></span>

<span data-ttu-id="d8964-128">![Entwurfs skizzieren](images/640px-sketch20170406.jpg)</span><span class="sxs-lookup"><span data-stu-id="d8964-128">![Design sketch](images/640px-sketch20170406.jpg)</span></span><br>
<span data-ttu-id="d8964-129">*Entwurfs skizzieren*</span><span class="sxs-lookup"><span data-stu-id="d8964-129">*Design sketches*</span></span>

<span data-ttu-id="d8964-130">In der Detailansicht wollte ich die Informationen der einzelnen Elemente mit einem gerenderten Text im 3D-Raum visualisieren.</span><span class="sxs-lookup"><span data-stu-id="d8964-130">In detail view, I wanted to visualize the information of each element with beautifully rendered text in 3D space.</span></span> <span data-ttu-id="d8964-131">Das animierte 3D-Rastermodell wird im Mittelpunkt angezeigt und kann aus unterschiedlichen Winkeln angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="d8964-131">The animated 3D electron model is displayed in the center area and can be viewed from different angles.</span></span>

![Interaktion](images/640px-periodictable-interaction.jpg)

<span data-ttu-id="d8964-133">![Prototypen](images/640px-periodictable-prototypes.jpg)</span><span class="sxs-lookup"><span data-stu-id="d8964-133">![Prototypes](images/640px-periodictable-prototypes.jpg)</span></span><br>
<span data-ttu-id="d8964-134">*Interaktionsprototypen*</span><span class="sxs-lookup"><span data-stu-id="d8964-134">*Interaction prototypes*</span></span>

<span data-ttu-id="d8964-135">Der Benutzer kann den Oberflächentyp ändern, indem er auf die Schaltflächen am unteren Rand der Tabelle tippt. Er kann zwischen Ebene, Zylinder, Kugel und Punkt wechseln.</span><span class="sxs-lookup"><span data-stu-id="d8964-135">The user can change the surface type by air tapping the buttons on the bottom of the table - they can switch between plane, cylinder, sphere, and scatter.</span></span>

## <a name="common-controls-and-patterns-used-in-this-app"></a><span data-ttu-id="d8964-136">Allgemeine Steuerelemente und Muster, die in dieser App verwendet werden</span><span class="sxs-lookup"><span data-stu-id="d8964-136">Common controls and patterns used in this app</span></span>

### <a name="interactable-object-button"></a><span data-ttu-id="d8964-137">Interagierbares Objekt (Schaltfläche)</span><span class="sxs-lookup"><span data-stu-id="d8964-137">Interactable object (button)</span></span>

<span data-ttu-id="d8964-138">[Ein interagierbares](../../design/interactable-object.md) Objekt ist ein Objekt, das auf grundlegende HoloLens-Eingaben reagieren kann.</span><span class="sxs-lookup"><span data-stu-id="d8964-138">[Interactable object](../../design/interactable-object.md) is an object, which can respond to basic HoloLens inputs.</span></span> <span data-ttu-id="d8964-139">Es wird als Prefab/Skript bereitgestellt, das Sie problemlos auf jedes Objekt anwenden können.</span><span class="sxs-lookup"><span data-stu-id="d8964-139">It's provided as a prefab/script, which you can easily apply to any object.</span></span> <span data-ttu-id="d8964-140">Sie können z. B. eine Kaffeetasse in Ihrer Szene interagierbar machen und auf Eingaben wie Anverkennung, Tippen in die Luft, Navigation und Manipulationsgesten reagieren.</span><span class="sxs-lookup"><span data-stu-id="d8964-140">For example, you can make a coffee cup in your scene interactable and respond to inputs such as gaze, air tap, navigation, and manipulation gestures.</span></span> [<span data-ttu-id="d8964-141">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="d8964-141">Learn more</span></span>](../../design/interactable-object.md)

![nteractable-Objekt](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a><span data-ttu-id="d8964-143">Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="d8964-143">Object collection</span></span>

<span data-ttu-id="d8964-144">[Die Objektsammlung](../../design/object-collection.md) ist ein Objekt, mit dem Sie mehrere Objekte in verschiedenen Formen gestalten können.</span><span class="sxs-lookup"><span data-stu-id="d8964-144">[Object collection](../../design/object-collection.md) is an object, which helps you lay out multiple objects in various shapes.</span></span> <span data-ttu-id="d8964-145">Sie unterstützt Ebene, Zylinder, Kugel und Punkt.</span><span class="sxs-lookup"><span data-stu-id="d8964-145">It supports plane, cylinder, sphere, and scatter.</span></span> <span data-ttu-id="d8964-146">Sie können zusätzliche Eigenschaften konfigurieren, z. B. Radius, Anzahl von Zeilen und Abstand.</span><span class="sxs-lookup"><span data-stu-id="d8964-146">You can configure additional properties such as radius, number of rows and the spacing.</span></span> [<span data-ttu-id="d8964-147">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="d8964-147">Learn more</span></span>](../../design/object-collection.md)

![Objektsammlung](images/640px-periodictable-collections.jpg)

## <a name="technical-details"></a><span data-ttu-id="d8964-149">Technische Details</span><span class="sxs-lookup"><span data-stu-id="d8964-149">Technical details</span></span>

<span data-ttu-id="d8964-150">Skripts und Prefabs für das Periodensystem der Elements-App finden Sie auf Mixed Reality [Design Labs GitHub.](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)</span><span class="sxs-lookup"><span data-stu-id="d8964-150">You can find scripts and prefabs for the Periodic Table of the Elements app on the [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span></span>

## <a name="porting-story-for-hololens-2"></a><span data-ttu-id="d8964-151">Portieren der Story für HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="d8964-151">Porting story for HoloLens 2</span></span>

<span data-ttu-id="d8964-152">Lesen Sie die Geschichte dazu, wie das Periodensystem der Elements-App mit HoloLens 2 instinktiven Interaktionen aktualisiert wurde.</span><span class="sxs-lookup"><span data-stu-id="d8964-152">Read the story on how Periodic Table of the Elements app was updated with HoloLens 2's instinctual interactions.</span></span>

[<span data-ttu-id="d8964-153">Periodensystem der Elemente 2.0</span><span class="sxs-lookup"><span data-stu-id="d8964-153">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)




## <a name="about-the-author"></a><span data-ttu-id="d8964-154">Informationen zum Autor</span><span class="sxs-lookup"><span data-stu-id="d8964-154">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="d8964-155"><b>Dong-Yoon-Park</b></span><span class="sxs-lookup"><span data-stu-id="d8964-155"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="d8964-156">UX-Designer @Microsoft</span><span class="sxs-lookup"><span data-stu-id="d8964-156">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="d8964-157">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="d8964-157">See also</span></span>

* <span data-ttu-id="d8964-158">[Hub für MRTK-Beispiele](/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [(Aus dem Microsoft Store in HoloLens 2 herunterladen)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span><span class="sxs-lookup"><span data-stu-id="d8964-158">[MRTK Examples Hub](/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span></span>
* <span data-ttu-id="d8964-159">[Oberflächen](sampleapp-surfaces.md) - [(Aus dem Microsoft Store in HoloLens 2 herunterladen)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span><span class="sxs-lookup"><span data-stu-id="d8964-159">[Surfaces](sampleapp-surfaces.md) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span></span>
* [<span data-ttu-id="d8964-160">Periodensystem der Elemente 2.0</span><span class="sxs-lookup"><span data-stu-id="d8964-160">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [<span data-ttu-id="d8964-161">Galaxy Explorer 2.0</span><span class="sxs-lookup"><span data-stu-id="d8964-161">Galaxy Explorer 2.0</span></span>](galaxy-explorer-update.md)