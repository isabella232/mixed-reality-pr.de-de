---
title: Oberflächen
description: Oberflächen ist eine Open-Source-Beispiel-App aus den Mixed Reality-Entwurfs Labors von Microsoft. Es wird erläutert, wie wir mit visuellen, Audiodaten und vollständig artikulierten Hand Nachverfolgung eine taktikvolle Sensation erstellen können.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: Gemischte Windows-Realität, Design, Beispiel-APP, Steuerelemente, mrtk, Mixed Reality Toolkit, Unity, Beispiel-apps, Beispiel-apps, Open Source, Microsoft Store, hololens, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: c20ea17b20c867d9bf1da0d5f6244e36f2abbf27
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678519"
---
# <a name="surfaces"></a><span data-ttu-id="b5f82-105">Oberflächen</span><span class="sxs-lookup"><span data-stu-id="b5f82-105">Surfaces</span></span>

>[!NOTE]
><span data-ttu-id="b5f82-106">In diesem Artikel wird ein exploratives Beispiel erläutert, das wir in den [Entwurfs Labors für gemischte Realität](https://github.com/Microsoft/MRDesignLabs_Unity)erstellt haben, einem Ort, an dem wir unsere Erkenntnisse und Vorschläge für die Entwicklung gemischter Reality-apps teilen.</span><span class="sxs-lookup"><span data-stu-id="b5f82-106">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="b5f82-107">Unsere Entwurfs bezogenen Artikel und Code werden sich weiterentwickeln, wenn wir neue Ermittlungen durchführen.</span><span class="sxs-lookup"><span data-stu-id="b5f82-107">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="b5f82-108">[Oberflächen](https://github.com/microsoft/MRDL_Unity_Surfaces)  ist eine Open-Source-Beispiel-App aus den Mixed Reality-Entwurfs Labors von Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b5f82-108">[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)  is an open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="b5f82-109">Es wird erläutert, wie wir mit visuellen, Audiodaten und vollständig artikulierten Hand Nachverfolgung eine taktikvolle Sensation erstellen können.</span><span class="sxs-lookup"><span data-stu-id="b5f82-109">It explores how we can create a tactile sensation with visual, audio, and fully articulated hand-tracking.</span></span>

![Oberflächen](images/MRDL_Surfaces_1.jpg)

## <a name="demo-video"></a><span data-ttu-id="b5f82-111">Demovideo</span><span class="sxs-lookup"><span data-stu-id="b5f82-111">Demo video</span></span> 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IhWQ]

<span data-ttu-id="b5f82-112">Aufgezeichnet mit hololens 2 mithilfe von Mixed Reality Capture</span><span class="sxs-lookup"><span data-stu-id="b5f82-112">Recorded with HoloLens 2 using Mixed Reality Capture</span></span>

## <a name="about-the-app"></a><span data-ttu-id="b5f82-113">Informationen zur APP</span><span class="sxs-lookup"><span data-stu-id="b5f82-113">About the app</span></span>
<span data-ttu-id="b5f82-114">Oberflächen zeigt, wie das Eingabe System von Mixed Reality Toolkit (mrtk) und die Bausteine zum Erstellen einer APP-Oberfläche für hololens 2 verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="b5f82-114">Surfaces demonstrates how to use Mixed Reality Toolkit(MRTK)'s input system and building blocks to create an app experience for HoloLens 2.</span></span> <span data-ttu-id="b5f82-115">In diesem Projekt finden Sie die Beispiele für:</span><span class="sxs-lookup"><span data-stu-id="b5f82-115">In this project, you can find the examples of:</span></span>
- <span data-ttu-id="b5f82-116">Verwenden Sie das [Eingabe System](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)von mrtk, insbesondere die Hand-und gemeinsame Nachverfolgung.</span><span class="sxs-lookup"><span data-stu-id="b5f82-116">Use MRTK's [Input System](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html), specifically hand / joint tracking.</span></span>
- <span data-ttu-id="b5f82-117">Verwenden Sie den [Standard-Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html) von mrtk für leistungsfähige Grafiken.</span><span class="sxs-lookup"><span data-stu-id="b5f82-117">Use MRTK's [Standard Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html) for performant graphics.</span></span>

<span data-ttu-id="b5f82-118">Sie können diese Projektkomponenten verwenden, um Ihre eigenen Umgebungen mit gemischter Reality-APP zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="b5f82-118">You can use this project's components to create your own mixed reality app experiences.</span></span>

## <a name="mr-dev-days-2020---learnings-from-the-mr-surfaces-app"></a><span data-ttu-id="b5f82-119">Mr dev Days 2020-Learnings von der App "Mr-Oberflächen"</span><span class="sxs-lookup"><span data-stu-id="b5f82-119">MR Dev Days 2020 - Learnings from the MR Surfaces App</span></span>
[<span data-ttu-id="b5f82-120">Erkenntnisse von der App "Mr-Oberflächen"</span><span class="sxs-lookup"><span data-stu-id="b5f82-120">Learnings from the MR Surfaces App</span></span>](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App)

<span data-ttu-id="b5f82-121">Lars Simkins, Senior Designer hinter der mrdl-Oberflächen-APP, spricht über die Entwurfs Story der APP und technische Highlights.</span><span class="sxs-lookup"><span data-stu-id="b5f82-121">Lars Simkins, Senior designer behind the MRDL Surfaces app talks about the app's design story and technical highlights.</span></span>

## <a name="project-repository-on-github"></a><span data-ttu-id="b5f82-122">Projektrepository auf GitHub</span><span class="sxs-lookup"><span data-stu-id="b5f82-122">Project repository on GitHub</span></span>
[https://github.com/microsoft/MRDL_Unity_Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)

## <a name="download-app-from-microsoft-store-in-hololens-2"></a><span data-ttu-id="b5f82-123">Herunterladen der APP aus Microsoft Store in hololens 2</span><span class="sxs-lookup"><span data-stu-id="b5f82-123">Download app from Microsoft Store in HoloLens 2</span></span>
https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0#activetab=pivot:overviewtab

<span data-ttu-id="b5f82-124">(Die APP ist nur auf hololens verfügbar 2)</span><span class="sxs-lookup"><span data-stu-id="b5f82-124">(The app is only available on HoloLens 2)</span></span>

## <a name="about-the-author"></a><span data-ttu-id="b5f82-125">Informationen zum Autor</span><span class="sxs-lookup"><span data-stu-id="b5f82-125">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="b5f82-126"><b>Dong-Yoon-Park</b></span><span class="sxs-lookup"><span data-stu-id="b5f82-126"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="b5f82-127">UX-Designer @Microsoft</span><span class="sxs-lookup"><span data-stu-id="b5f82-127">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="b5f82-128">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="b5f82-128">See also</span></span>

* <span data-ttu-id="b5f82-129">[Hub für MRTK-Beispiele](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ExampleHub.html) - [(Aus dem Microsoft Store in HoloLens 2 herunterladen)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span><span class="sxs-lookup"><span data-stu-id="b5f82-129">[MRTK Examples Hub](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ExampleHub.html) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span></span>
* <span data-ttu-id="b5f82-130">[Oberflächen](sampleapp-surfaces.md) - [(Aus dem Microsoft Store in HoloLens 2 herunterladen)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span><span class="sxs-lookup"><span data-stu-id="b5f82-130">[Surfaces](sampleapp-surfaces.md) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span></span>
* [<span data-ttu-id="b5f82-131">Periodensystem der Elemente 2.0</span><span class="sxs-lookup"><span data-stu-id="b5f82-131">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [<span data-ttu-id="b5f82-132">Galaxy Explorer 2.0</span><span class="sxs-lookup"><span data-stu-id="b5f82-132">Galaxy Explorer 2.0</span></span>](galaxy-explorer-update.md)
