---
title: Oberflächen
description: Erfahren Sie, wie Sie in der Beispiel-App für Oberflächen mit visuellen, Audio-und Hand zeitast-und Hand zeitast-
author: cre8ivepark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: Gemischte Windows-Realität, Design, Beispiel-APP, Steuerelemente, mrtk, Mixed Reality Toolkit, Unity, Beispiel-apps, Beispiel-apps, Open Source, Microsoft Store, hololens, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 0e75a72ec518dea3513b6868aec56d1c7c89bd05
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300135"
---
# <a name="surfaces"></a><span data-ttu-id="e181e-104">Oberflächen</span><span class="sxs-lookup"><span data-stu-id="e181e-104">Surfaces</span></span>

>[!NOTE]
><span data-ttu-id="e181e-105">In diesem Artikel wird ein exploratives Beispiel erläutert, das wir in den [Entwurfs Labors für gemischte Realität](https://github.com/Microsoft/MRDesignLabs_Unity)erstellt haben, einem Ort, an dem wir unsere Erkenntnisse und Vorschläge für die Entwicklung gemischter Reality-apps teilen.</span><span class="sxs-lookup"><span data-stu-id="e181e-105">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="e181e-106">Unsere Entwurfs bezogenen Artikel und Code werden sich weiterentwickeln, wenn wir neue Ermittlungen durchführen.</span><span class="sxs-lookup"><span data-stu-id="e181e-106">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="e181e-107">[Oberflächen](https://github.com/microsoft/MRDL_Unity_Surfaces)  ist eine Open-Source-Beispiel-App aus den Mixed Reality-Entwurfs Labors von Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e181e-107">[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)  is an open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="e181e-108">Es wird erläutert, wie wir mit visuellen, Audiodaten und vollständig artikulierten Hand Nachverfolgung eine taktikvolle Sensation erstellen können.</span><span class="sxs-lookup"><span data-stu-id="e181e-108">It explores how we can create a tactile sensation with visual, audio, and fully articulated hand-tracking.</span></span>

![Oberflächen](images/MRDL_Surfaces_1.jpg)

## <a name="demo-video"></a><span data-ttu-id="e181e-110">Demovideo</span><span class="sxs-lookup"><span data-stu-id="e181e-110">Demo video</span></span> 

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IhWQ]

<span data-ttu-id="e181e-111">Aufgezeichnet mit hololens 2 mithilfe von Mixed Reality Capture</span><span class="sxs-lookup"><span data-stu-id="e181e-111">Recorded with HoloLens 2 using Mixed Reality Capture</span></span>

## <a name="about-the-app"></a><span data-ttu-id="e181e-112">Informationen zur APP</span><span class="sxs-lookup"><span data-stu-id="e181e-112">About the app</span></span>

<span data-ttu-id="e181e-113">Oberflächen zeigt, wie das Eingabe System von Mixed Reality Toolkit (mrtk) und die Bausteine zum Erstellen einer APP-Oberfläche für hololens 2 verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="e181e-113">Surfaces demonstrates how to use Mixed Reality Toolkit(MRTK)'s input system and building blocks to create an app experience for HoloLens 2.</span></span> <span data-ttu-id="e181e-114">In diesem Projekt finden Sie die Beispiele für:</span><span class="sxs-lookup"><span data-stu-id="e181e-114">In this project, you can find the examples of:</span></span>

- <span data-ttu-id="e181e-115">Verwenden Sie das [Eingabe System](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/input/overview)von mrtk, insbesondere die Hand-und gemeinsame Nachverfolgung.</span><span class="sxs-lookup"><span data-stu-id="e181e-115">Use MRTK's [Input System](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/input/overview), specifically hand / joint tracking.</span></span>
- <span data-ttu-id="e181e-116">Verwenden Sie den [Standard-Shader](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader) von mrtk für leistungsfähige Grafiken.</span><span class="sxs-lookup"><span data-stu-id="e181e-116">Use MRTK's [Standard Shader](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader) for performant graphics.</span></span>

<span data-ttu-id="e181e-117">Sie können diese Projektkomponenten verwenden, um Ihre eigenen Umgebungen mit gemischter Reality-APP zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="e181e-117">You can use this project's components to create your own mixed reality app experiences.</span></span>

## <a name="mr-dev-days-2020---learnings-from-the-mr-surfaces-app"></a><span data-ttu-id="e181e-118">Mr dev Days 2020-Learnings von der App "Mr-Oberflächen"</span><span class="sxs-lookup"><span data-stu-id="e181e-118">MR Dev Days 2020 - Learnings from the MR Surfaces App</span></span>

[<span data-ttu-id="e181e-119">Erkenntnisse von der App "Mr-Oberflächen"</span><span class="sxs-lookup"><span data-stu-id="e181e-119">Learnings from the MR Surfaces App</span></span>](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App)

<span data-ttu-id="e181e-120">Lars Simkins, Senior Designer hinter der mrdl-Oberflächen-APP, spricht über die Entwurfs Story der APP und technische Highlights.</span><span class="sxs-lookup"><span data-stu-id="e181e-120">Lars Simkins, Senior designer behind the MRDL Surfaces app talks about the app's design story and technical highlights.</span></span>

## <a name="project-repository-on-github"></a><span data-ttu-id="e181e-121">Projektrepository auf GitHub</span><span class="sxs-lookup"><span data-stu-id="e181e-121">Project repository on GitHub</span></span>

[https://github.com/microsoft/MRDL_Unity_Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)

## <a name="download-app-from-microsoft-store-in-hololens-2"></a><span data-ttu-id="e181e-122">Herunterladen der APP aus Microsoft Store in hololens 2</span><span class="sxs-lookup"><span data-stu-id="e181e-122">Download app from Microsoft Store in HoloLens 2</span></span>

https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0#activetab=pivot:overviewtab

<span data-ttu-id="e181e-123">(Die APP ist nur auf hololens verfügbar 2)</span><span class="sxs-lookup"><span data-stu-id="e181e-123">(The app is only available on HoloLens 2)</span></span>

## <a name="about-the-author"></a><span data-ttu-id="e181e-124">Informationen zum Autor</span><span class="sxs-lookup"><span data-stu-id="e181e-124">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="e181e-125"><b>Dong-Yoon-Park</b></span><span class="sxs-lookup"><span data-stu-id="e181e-125"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="e181e-126">UX-Designer @Microsoft</span><span class="sxs-lookup"><span data-stu-id="e181e-126">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="e181e-127">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e181e-127">See also</span></span>

* <span data-ttu-id="e181e-128">[Hub für MRTK-Beispiele](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [(Aus dem Microsoft Store in HoloLens 2 herunterladen)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span><span class="sxs-lookup"><span data-stu-id="e181e-128">[MRTK Examples Hub](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span></span>
* <span data-ttu-id="e181e-129">[Oberflächen](sampleapp-surfaces.md) - [(Aus dem Microsoft Store in HoloLens 2 herunterladen)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span><span class="sxs-lookup"><span data-stu-id="e181e-129">[Surfaces](sampleapp-surfaces.md) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span></span>
* [<span data-ttu-id="e181e-130">Periodensystem der Elemente 2.0</span><span class="sxs-lookup"><span data-stu-id="e181e-130">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [<span data-ttu-id="e181e-131">Galaxy Explorer 2.0</span><span class="sxs-lookup"><span data-stu-id="e181e-131">Galaxy Explorer 2.0</span></span>](galaxy-explorer-update.md)
