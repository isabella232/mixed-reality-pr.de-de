---
title: Oberflächen
description: Erfahren Sie, wie Sie in der Beispiel-App Oberflächen taktile Hefte mit Visuellem, Audio und artikuliertem Handtracking erstellen.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: Windows Mixed Reality, Entwurf, Beispiel-App, Steuerelemente, MRTK, Mixed Reality Toolkit, Unity, Beispiel-Apps, Beispiel-Apps, Open Source, Microsoft Store, HoloLens, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 28f8bc1e1f30573936067a83b1ad26133c23c5b8
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2021
ms.locfileid: "110743390"
---
# <a name="surfaces"></a><span data-ttu-id="07e51-104">Oberflächen</span><span class="sxs-lookup"><span data-stu-id="07e51-104">Surfaces</span></span>

>[!NOTE]
><span data-ttu-id="07e51-105">In diesem Artikel wird ein exploratives Beispiel erläutert, das wir in den [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity)erstellt haben, einem Ort, an dem wir unsere Erkenntnisse und Vorschläge für die Entwicklung von Mixed Reality-Apps teilen.</span><span class="sxs-lookup"><span data-stu-id="07e51-105">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="07e51-106">Unsere artikel- und codebezogenen Entwurfsartikel werden sich weiterentwickeln, wenn wir neue Ermittlungen vornehmen.</span><span class="sxs-lookup"><span data-stu-id="07e51-106">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="07e51-107">[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)  ist eine Open-Source-Beispiel-App aus den Mixed Reality Design Labs von Microsoft.</span><span class="sxs-lookup"><span data-stu-id="07e51-107">[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)  is an open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="07e51-108">Es wird untersucht, wie wir einen taktilen Hefter mit visuellen, Audio- und vollständig formulierten Handtrackings erstellen können.</span><span class="sxs-lookup"><span data-stu-id="07e51-108">It explores how we can create a tactile sensation with visual, audio, and fully articulated hand-tracking.</span></span>

![Oberflächen](images/MRDL_Surfaces_1.jpg)

## <a name="demo-video"></a><span data-ttu-id="07e51-110">Demovideo</span><span class="sxs-lookup"><span data-stu-id="07e51-110">Demo video</span></span> 

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IhWQ]

<span data-ttu-id="07e51-111">Aufgezeichnet mit HoloLens 2 mithilfe von Mixed Reality-Aufnahme</span><span class="sxs-lookup"><span data-stu-id="07e51-111">Recorded with HoloLens 2 using Mixed Reality Capture</span></span>

## <a name="about-the-app"></a><span data-ttu-id="07e51-112">Informationen zur App</span><span class="sxs-lookup"><span data-stu-id="07e51-112">About the app</span></span>

<span data-ttu-id="07e51-113">Oberflächen veranschaulichen die Verwendung des Eingabesystems und der Bausteine von Mixed Reality Toolkit (MRTK), um eine App-Erfahrung für HoloLens 2 zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="07e51-113">Surfaces demonstrates how to use Mixed Reality Toolkit(MRTK)'s input system and building blocks to create an app experience for HoloLens 2.</span></span> <span data-ttu-id="07e51-114">In diesem Projekt finden Sie beispiele für:</span><span class="sxs-lookup"><span data-stu-id="07e51-114">In this project, you can find the examples of:</span></span>

- <span data-ttu-id="07e51-115">Verwenden Sie das [MRTK-Eingabesystem,](/windows/mixed-reality/mrtk-unity/features/input/overview)insbesondere hand-/joint tracking.</span><span class="sxs-lookup"><span data-stu-id="07e51-115">Use MRTK's [Input System](/windows/mixed-reality/mrtk-unity/features/input/overview), specifically hand / joint tracking.</span></span>
- <span data-ttu-id="07e51-116">Verwenden Sie den [Standard-Shader](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader) von MRTK für performante Grafiken.</span><span class="sxs-lookup"><span data-stu-id="07e51-116">Use MRTK's [Standard Shader](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader) for performant graphics.</span></span>

<span data-ttu-id="07e51-117">Sie können die Komponenten dieses Projekts verwenden, um Ihre eigenen Mixed Reality-App-Erfahrungen zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="07e51-117">You can use this project's components to create your own mixed reality app experiences.</span></span>

## <a name="mr-dev-days-2020---learnings-from-the-mr-surfaces-app"></a><span data-ttu-id="07e51-118">MR Dev Days 2020 – Erkenntnisse aus der MR-Oberflächen-App</span><span class="sxs-lookup"><span data-stu-id="07e51-118">MR Dev Days 2020 - Learnings from the MR Surfaces App</span></span>

[<span data-ttu-id="07e51-119">Erkenntnisse aus der MR-Oberflächen-App</span><span class="sxs-lookup"><span data-stu-id="07e51-119">Learnings from the MR Surfaces App</span></span>](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App)

<span data-ttu-id="07e51-120">Dieser Senior Designer hinter der APP FÜRL-Oberflächen spricht über die Designstory und die technischen Highlights der App.</span><span class="sxs-lookup"><span data-stu-id="07e51-120">Lars Simkins, Senior designer behind the MRDL Surfaces app talks about the app's design story and technical highlights.</span></span>

## <a name="project-repository-on-github"></a><span data-ttu-id="07e51-121">Projekt-Repository auf GitHub</span><span class="sxs-lookup"><span data-stu-id="07e51-121">Project repository on GitHub</span></span>

[https://github.com/microsoft/MRDL_Unity_Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)

## <a name="download-app-from-microsoft-store-in-hololens-2"></a><span data-ttu-id="07e51-122">Herunterladen der App aus Microsoft Store in HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="07e51-122">Download app from Microsoft Store in HoloLens 2</span></span>

https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0#activetab=pivot:overviewtab

<span data-ttu-id="07e51-123">(Die App ist nur auf HoloLens 2 verfügbar.)</span><span class="sxs-lookup"><span data-stu-id="07e51-123">(The app is only available on HoloLens 2)</span></span>

## <a name="about-the-author"></a><span data-ttu-id="07e51-124">Informationen zum Autor</span><span class="sxs-lookup"><span data-stu-id="07e51-124">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="07e51-125"><b>Dong-Yoon-Park</b></span><span class="sxs-lookup"><span data-stu-id="07e51-125"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="07e51-126">UX-Designer @Microsoft</span><span class="sxs-lookup"><span data-stu-id="07e51-126">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="07e51-127">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="07e51-127">See also</span></span>

* <span data-ttu-id="07e51-128">[Hub für MRTK-Beispiele](/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [(Aus dem Microsoft Store in HoloLens 2 herunterladen)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span><span class="sxs-lookup"><span data-stu-id="07e51-128">[MRTK Examples Hub](/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span></span>
* <span data-ttu-id="07e51-129">[Oberflächen](sampleapp-surfaces.md) - [(Aus dem Microsoft Store in HoloLens 2 herunterladen)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span><span class="sxs-lookup"><span data-stu-id="07e51-129">[Surfaces](sampleapp-surfaces.md) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span></span>
* [<span data-ttu-id="07e51-130">Periodensystem der Elemente 2.0</span><span class="sxs-lookup"><span data-stu-id="07e51-130">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [<span data-ttu-id="07e51-131">Galaxy Explorer 2.0</span><span class="sxs-lookup"><span data-stu-id="07e51-131">Galaxy Explorer 2.0</span></span>](galaxy-explorer-update.md)