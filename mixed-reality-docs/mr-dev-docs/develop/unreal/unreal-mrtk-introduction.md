---
title: Einführung in MRTK für Unreal
description: Machen Sie Ihre ersten Schritte mit allem, was das Mixed Reality-Toolkit für Unreal für neue Mixed Reality-Entwickler bereithält.
author: hferrone
ms.author: v-hferrone
ms.date: 01/08/2021
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, Test, Mixed Reality Toolkit, MRTK-Version 2, MRTK, Tools, SDK, HoloLens, HoloLens 2, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, plattformübergreifend
ms.openlocfilehash: 3d46b92dbf3182ca5a50a8e106d2b947e4f7120f
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394284"
---
# <a name="introducing-mrtk-for-unreal"></a><span data-ttu-id="92e15-104">Einführung in MRTK für Unreal</span><span class="sxs-lookup"><span data-stu-id="92e15-104">Introducing MRTK for Unreal</span></span>

![MRTK-Bannerbild](../../design/images/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="92e15-106">Was ist das Mixed Reality Toolkit (MRTK)?</span><span class="sxs-lookup"><span data-stu-id="92e15-106">What is Mixed Reality Toolkit (MRTK)?</span></span>

<span data-ttu-id="92e15-107">MRTK ist ein fantastisches Open-Source-Toolkit, das seit der ersten Veröffentlichung der HoloLens verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="92e15-107">MRTK is an amazing open-source toolkit that has been around since the HoloLens was first released.</span></span> <span data-ttu-id="92e15-108">Das Toolkit wäre nicht so weit, wie es heute ist, ohne die harte Arbeit unserer mitwirkenden Entwicklercommunity.</span><span class="sxs-lookup"><span data-stu-id="92e15-108">The toolkit wouldn't be where it is today without the hard work of our contributing developer community.</span></span> 

<span data-ttu-id="92e15-109">Das Mixed Reality-Toolkit für Unreal (MRTK-Unreal) umfasst eine Reihe von Komponenten in Form von Plug-Ins, Beispielen und Dokumentationsmaterial, um die Entwicklung von Mixed Reality-Anwendungen mit der Unreal Engine zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="92e15-109">The Mixed Reality Toolkit for Unreal (MRTK-Unreal) is a set of components, in the form of plugins, samples and documentation, designed to help development of Mixed Reality applications using the Unreal Engine.</span></span> <span data-ttu-id="92e15-110">Das Toolkit besteht derzeit aus Folgendem:</span><span class="sxs-lookup"><span data-stu-id="92e15-110">Currently, the toolkit consists of:</span></span>
* <span data-ttu-id="92e15-111">[UX-Tools für Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal), das Code, Blaupausen und Beispiele bereitstellt, um UX-Funktionen für HoloLens 2-Anwendungen zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="92e15-111">[UX Tools for Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal), which provides code, blueprints, and examples to implement UX features for Hololens 2 applications.</span></span>
* <span data-ttu-id="92e15-112">[Grafiktools für Unreal](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal), das hilft, die visuelle Genauigkeit von Mixed Reality-Anwendungen zu verbessern und gleichzeitig Leistungsbudgets einzuhalten.</span><span class="sxs-lookup"><span data-stu-id="92e15-112">[Graphics Tools for Unreal](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal), which helps improve the visual fidelity of Mixed Reality applications while staying within performance budgets.</span></span>

<span data-ttu-id="92e15-113">Werfen Sie einen Blick in die [MRTK-Dokumentation auf GitHub](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html), und beginnen Sie mit den Installationsanleitungen für [UX-Tools](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html) oder [Grafiktools](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md).</span><span class="sxs-lookup"><span data-stu-id="92e15-113">Take a look at [MRTK's documentation on GitHub](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html) and get started with [UX Tools](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html) or [Graphics Tools](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md) installation guides.</span></span>

### <a name="modular"></a><span data-ttu-id="92e15-114">Modular</span><span class="sxs-lookup"><span data-stu-id="92e15-114">Modular</span></span>

<span data-ttu-id="92e15-115">Wir haben MRTK Unreal modular aufgebaut, es ist also nicht notwendig, jeden Teil des Toolkits in Ihr Projekt zu integrieren.</span><span class="sxs-lookup"><span data-stu-id="92e15-115">We've built MRTK Unreal in a modular way, so you don't need to take every bit of the toolkit into your project.</span></span> <span data-ttu-id="92e15-116">Sie können die benötigten Plug-Ins auswählen und sie jederzeit hinzufügen oder entfernen.</span><span class="sxs-lookup"><span data-stu-id="92e15-116">You can pick and choose the plugins you need, and add or remove them whenever you see fit.</span></span> <span data-ttu-id="92e15-117">Dieser Ansatz verringert die Größe Ihres Projekts und vereinfacht seine Verwaltung.</span><span class="sxs-lookup"><span data-stu-id="92e15-117">This approach keeps your project size smaller and makes it easier to manage.</span></span>  

### <a name="performant"></a><span data-ttu-id="92e15-118">Leistungsfähig</span><span class="sxs-lookup"><span data-stu-id="92e15-118">Performant</span></span>

<span data-ttu-id="92e15-119">Für das Arbeiten mit mobilen Plattformen haben wir MRTK Unter mit dem Augenmerk auf Leistung aufgebaut.</span><span class="sxs-lookup"><span data-stu-id="92e15-119">Working with mobile platforms, we constructed MRTK Unreal with performance in mind.</span></span> <span data-ttu-id="92e15-120">Das ist äußerst wichtig, und wir wollten sicherstellen, dass die Tools sich Ihnen nicht in den Weg stellen.</span><span class="sxs-lookup"><span data-stu-id="92e15-120">This is super important and we wanted to ensure that the tools aren't going to work against you.</span></span>

## <a name="project-setup"></a><span data-ttu-id="92e15-121">Projekteinrichtung</span><span class="sxs-lookup"><span data-stu-id="92e15-121">Project setup</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="92e15-122">Unreal-Engine und MRTK herunterladen</span><span class="sxs-lookup"><span data-stu-id="92e15-122">Download Unreal Engine and MRTK</span></span>](unreal-project-setup.md)

## <a name="see-also"></a><span data-ttu-id="92e15-123">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="92e15-123">See also</span></span>

* [<span data-ttu-id="92e15-124">Installieren der Tools</span><span class="sxs-lookup"><span data-stu-id="92e15-124">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="92e15-125">Entwickeln mit MRTK für Unreal</span><span class="sxs-lookup"><span data-stu-id="92e15-125">Developing with MRTK for Unreal</span></span>](unreal-development-overview.md)
* [<span data-ttu-id="92e15-126">UX-Tools – Installationshandbuch (GitHub)</span><span class="sxs-lookup"><span data-stu-id="92e15-126">UX Tools - Installation guide (GitHub)</span></span>](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html)
* [<span data-ttu-id="92e15-127">UX-Tools – Startseite der Dokumentation (GitHub)</span><span class="sxs-lookup"><span data-stu-id="92e15-127">UX Tools- Documentation home (GitHub)</span></span>](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html)
* [<span data-ttu-id="92e15-128">Grafiktools – Installationshandbuch (GitHub)</span><span class="sxs-lookup"><span data-stu-id="92e15-128">Graphics Tools - Installation guide (GitHub)</span></span>](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md)
* [<span data-ttu-id="92e15-129">Grafiktools – Startseite der Dokumentation (GitHub)</span><span class="sxs-lookup"><span data-stu-id="92e15-129">Graphics Tools - Documentation home (GitHub)</span></span>](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/)