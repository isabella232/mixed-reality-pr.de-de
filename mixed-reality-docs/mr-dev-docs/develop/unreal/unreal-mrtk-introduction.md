---
title: Einführung in MRTK für Unreal
description: Machen Sie Ihre ersten Schritte mit allem, was das Mixed Reality-Toolkit für Unreal für neue Mixed Reality-Entwickler bereithält.
author: hferrone
ms.author: v-hferrone
ms.date: 01/08/2021
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, Test, Mixed Reality Toolkit, MRTK-Version 2, MRTK, Tools, SDK, HoloLens, HoloLens 2, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, plattformübergreifend
ms.openlocfilehash: 4aa21cbee75c4c362abfd609add922ad9c922682
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2021
ms.locfileid: "98584749"
---
# <a name="introducing-mrtk-for-unreal"></a><span data-ttu-id="a0c6a-104">Einführung in MRTK für Unreal</span><span class="sxs-lookup"><span data-stu-id="a0c6a-104">Introducing MRTK for Unreal</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="a0c6a-106">Was ist das Mixed Reality Toolkit (MRTK)?</span><span class="sxs-lookup"><span data-stu-id="a0c6a-106">What is Mixed Reality Toolkit (MRTK)?</span></span>

<span data-ttu-id="a0c6a-107">MRTK ist ein fantastisches Open-Source-Toolkit, das seit der ersten Veröffentlichung der HoloLens verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-107">MRTK is an amazing open-source toolkit that has been around since the HoloLens was first released.</span></span> <span data-ttu-id="a0c6a-108">Das Toolkit wäre nicht so weit, wie es heute ist, ohne die harte Arbeit unserer mitwirkenden Entwicklercommunity.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-108">The toolkit wouldn't be where it is today without the hard work of our contributing developer community.</span></span> 

<span data-ttu-id="a0c6a-109">Das Mixed Reality-Toolkit für Unreal (MRTK-Unreal) umfasst eine Reihe von Komponenten in Form von Plug-Ins, Beispielen und Dokumentationsmaterial, um die Entwicklung von Mixed Reality-Anwendungen mit der Unreal Engine zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-109">The Mixed Reality Toolkit for Unreal (MRTK-Unreal) is a set of components, in the form of plugins, samples and documentation, designed to help development of Mixed Reality applications using the Unreal Engine.</span></span> <span data-ttu-id="a0c6a-110">Das Toolkit besteht derzeit aus Folgendem:</span><span class="sxs-lookup"><span data-stu-id="a0c6a-110">Currently, the toolkit consists of:</span></span>
* <span data-ttu-id="a0c6a-111">[UX-Tools für Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal), das Code, Blaupausen und Beispiele bereitstellt, um UX-Funktionen für HoloLens 2-Anwendungen zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-111">[UX Tools for Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal), which provides code, blueprints, and examples to implement UX features for Hololens 2 applications.</span></span>
* <span data-ttu-id="a0c6a-112">[Grafiktools für Unreal](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal), das hilft, die visuelle Genauigkeit von Mixed Reality-Anwendungen zu verbessern und gleichzeitig Leistungsbudgets einzuhalten.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-112">[Graphics Tools for Unreal](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal), which helps improve the visual fidelity of Mixed Reality applications while staying within performance budgets.</span></span>

<br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCG]

<span data-ttu-id="a0c6a-113">Werfen Sie einen Blick in die [MRTK-Dokumentation auf GitHub](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html), und beginnen Sie mit den Installationsanleitungen für [UX-Tools](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html) oder [Grafiktools](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md).</span><span class="sxs-lookup"><span data-stu-id="a0c6a-113">Take a look at [MRTK's documentation on GitHub](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html) and get started with [UX Tools](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html) or [Graphics Tools](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md) installation guides.</span></span>

### <a name="modular"></a><span data-ttu-id="a0c6a-114">Modular</span><span class="sxs-lookup"><span data-stu-id="a0c6a-114">Modular</span></span>

<span data-ttu-id="a0c6a-115">Wir haben MRTK Unreal modular aufgebaut, es ist also nicht notwendig, jeden Teil des Toolkits in Ihr Projekt zu integrieren.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-115">We've built MRTK Unreal in a modular way, so you don't need to take every bit of the toolkit into your project.</span></span> <span data-ttu-id="a0c6a-116">Sie können die benötigten Plug-Ins auswählen und sie jederzeit hinzufügen oder entfernen.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-116">You can pick and choose the plugins you need, and add or remove them whenever you see fit.</span></span> <span data-ttu-id="a0c6a-117">Dieser Ansatz verringert die Größe Ihres Projekts und vereinfacht seine Verwaltung.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-117">This approach keeps your project size smaller and makes it easier to manage.</span></span>  

### <a name="performant"></a><span data-ttu-id="a0c6a-118">Leistungsfähig</span><span class="sxs-lookup"><span data-stu-id="a0c6a-118">Performant</span></span>

<span data-ttu-id="a0c6a-119">Für das Arbeiten mit mobilen Plattformen haben wir MRTK Unter mit dem Augenmerk auf Leistung aufgebaut.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-119">Working with mobile platforms, we constructed MRTK Unreal with performance in mind.</span></span> <span data-ttu-id="a0c6a-120">Das ist äußerst wichtig, und wir wollten sicherstellen, dass die Tools sich Ihnen nicht in den Weg stellen.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-120">This is super important and we wanted to ensure that the tools aren't going to work against you.</span></span>

## <a name="see-also"></a><span data-ttu-id="a0c6a-121">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="a0c6a-121">See also</span></span>

* [<span data-ttu-id="a0c6a-122">Installieren der Tools</span><span class="sxs-lookup"><span data-stu-id="a0c6a-122">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="a0c6a-123">Entwickeln mit MRTK für Unreal</span><span class="sxs-lookup"><span data-stu-id="a0c6a-123">Developing with MRTK for Unreal</span></span>](unreal-development-overview.md)
* [<span data-ttu-id="a0c6a-124">UX-Tools – Installationshandbuch (GitHub)</span><span class="sxs-lookup"><span data-stu-id="a0c6a-124">UX Tools - Installation guide (GitHub)</span></span>](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html)
* [<span data-ttu-id="a0c6a-125">UX-Tools – Startseite der Dokumentation (GitHub)</span><span class="sxs-lookup"><span data-stu-id="a0c6a-125">UX Tools- Documentation home (GitHub)</span></span>](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html)
* [<span data-ttu-id="a0c6a-126">Grafiktools – Installationshandbuch (GitHub)</span><span class="sxs-lookup"><span data-stu-id="a0c6a-126">Graphics Tools - Installation guide (GitHub)</span></span>](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md)
* [<span data-ttu-id="a0c6a-127">Grafiktools – Startseite der Dokumentation (GitHub)</span><span class="sxs-lookup"><span data-stu-id="a0c6a-127">Graphics Tools - Documentation home (GitHub)</span></span>](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/)