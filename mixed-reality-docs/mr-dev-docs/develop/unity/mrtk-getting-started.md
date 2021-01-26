---
title: Einführung in MRTK für Unity
description: Machen Sie Ihre ersten Schritte mit allem, was das plattformübergreifende Mixed Reality-Toolkit für neue Mixed Reality-Entwickler bereithält.
author: cre8ivepark
ms.author: dongpark
ms.date: 05/15/2019
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, Test, Mixed Reality Toolkit, MRTK-Version 2, MRTK, Tools, SDK, HoloLens, HoloLens 2, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, plattformübergreifend
ms.openlocfilehash: 4c013f1fa50518404f899b4181e7c07b9e4e0e56
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581700"
---
# <a name="introducing-mrtk-for-unity"></a><span data-ttu-id="d6bf8-104">Einführung in MRTK für Unity</span><span class="sxs-lookup"><span data-stu-id="d6bf8-104">Introducing MRTK for Unity</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="d6bf8-106">Was ist das Mixed Reality Toolkit (MRTK)?</span><span class="sxs-lookup"><span data-stu-id="d6bf8-106">What is Mixed Reality Toolkit (MRTK)?</span></span>

<span data-ttu-id="d6bf8-107">MRTK ist ein fantastisches Open-Source-Toolkit, das seit der ersten Veröffentlichung der HoloLens verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-107">MRTK is an amazing open-source toolkit that has been around since the HoloLens was first released.</span></span> <span data-ttu-id="d6bf8-108">Das Toolkit wäre nicht so weit, wie es heute ist, ohne die harte Arbeit unserer mitwirkenden Entwicklercommunity.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-108">The toolkit wouldn't be where it is today without the hard work of our contributing developer community.</span></span> <span data-ttu-id="d6bf8-109">In Lauf der letzten drei Jahre haben wir auf das Feedback unserer Entwicklercommunity gehört und MRTK v2 aufgebaut, um den größten Bedenken Rechnung zu tragen.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-109">Over the past three years, we've listened to the feedback of our developer community, and built MRTK v2 to take the biggest concerns into account.</span></span>  

<span data-ttu-id="d6bf8-110">MRTK für Unity ist ein plattformübergreifendes Open Source-Entwicklungskit für Mixed Reality-Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-110">MRTK for Unity is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="d6bf8-111">Das Toolkit bietet ein plattformübergreifendes Eingabesystem, Grundlagenkomponenten und gemeinsame Bausteine für räumliche Interaktionen.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-111">The toolkit provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="d6bf8-112">MRTK, Version 2, soll die Anwendungsentwicklung für Microsoft HoloLens, für immersive Windows Mixed Reality-Headsets (VR) und für die OpenVR-Plattform beschleunigen.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-112">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="d6bf8-113">Das Projekt ist darauf ausgerichtet, die Einstiegshürden zum Erstellen von Mixed Reality-Anwendungen zu verringern, und einen Beitrag für die Community auf diesem stetig wachsenden Gebiet zu leisten.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-113">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

<br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCG]

<span data-ttu-id="d6bf8-114">Werfen Sie einen Blick in die [MRTK-Dokumentation auf GitHub](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html), und beginnen Sie mit der [Installationsanleitung](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html).</span><span class="sxs-lookup"><span data-stu-id="d6bf8-114">Take a look at [MRTK's documentation on GitHub](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) and get started with the [installation guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html).</span></span>

## <a name="new-with-mrtk-v2"></a><span data-ttu-id="d6bf8-115">Neu in MRTK v2</span><span class="sxs-lookup"><span data-stu-id="d6bf8-115">New with MRTK v2</span></span>

<span data-ttu-id="d6bf8-116">Wir möchten unser andauerndes Engagement für diese Plattformtools betonen.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-116">We want to stress our commitment to these platform tools.</span></span>  <span data-ttu-id="d6bf8-117">Tatsächlich haben wir das MRTK, Version 2, verwendet, um unsere Inbox-Erlebnisse zu entwickeln, wie etwa die vorgefertigte Setup-Erfahrung (OOBE) und unsere Mixed Reality-Tipps-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-117">In fact, we used MRTK version 2 to develop our inbox experiences, such as the out-of-box setup experience (OOBE) and our Mixed Reality Tips application.</span></span> <span data-ttu-id="d6bf8-118">Sie können außerdem damit rechnen, dass neue Funktionen von HoloLens 2 erstmalig über das MRTK verfügbar gemacht werden, da wir glauben, dies ist der richtige Weg für die Entwicklung unserer Plattform.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-118">You can also expect to see new HoloLens 2 capabilities first exposed through MRTK because we believe it’s the best way to develop on our platform.</span></span> 

### <a name="modular"></a><span data-ttu-id="d6bf8-119">Modular</span><span class="sxs-lookup"><span data-stu-id="d6bf8-119">Modular</span></span>

<span data-ttu-id="d6bf8-120">Wir haben das Toolkit modular aufgebaut, es ist also nicht notwendig, jeden Teil des Toolkits in Ihr Projekt zu integrieren.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-120">We have built it in a modular way, so you don't need to take every bit of the toolkit into your project.</span></span>  <span data-ttu-id="d6bf8-121">Dies bietet in der Praxis eine Reihe von Vorteilen.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-121">There are actually a few benefits to this.</span></span>  <span data-ttu-id="d6bf8-122">Es verringert die Größe Ihres Projekts und vereinfacht seine Verwaltung.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-122">It keeps your project size smaller, and makes it easier to manage.</span></span>  <span data-ttu-id="d6bf8-123">Da es aus skriptfähigen Objekten aufgebaut wurde und über eine Schnittstelle gesteuert wird, können Sie außerdem die enthaltenen Komponenten durch eigene ersetzen, um andere Dienste, Systeme und Plattformen zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-123">Additionally, because it’s built with scriptable objects and is interface-driven, it’s also possible for you to replace the components that are included with your own, to support other services, systems, and platforms.</span></span>

### <a name="cross-platform"></a><span data-ttu-id="d6bf8-124">Plattformübergreifend</span><span class="sxs-lookup"><span data-stu-id="d6bf8-124">Cross-platform</span></span>

<span data-ttu-id="d6bf8-125">Andere Plattformen sind ein Thema, denn das Toolkit bietet plattformübergreifende Unterstützung.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-125">Speaking of other platforms, it has cross-platform support.</span></span>  <span data-ttu-id="d6bf8-126">Das bedeutet zwar nicht, dass jede einzelne Plattform unterstützt wird, wir haben aber sichergestellt, dass der Code des Toolkits auch dann funktioniert, wenn Sie ihr Buildziel auf eine andere Plattform umstellen.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-126">And while this doesn’t mean every single platform is supported, we have made sure none of the toolkit code will break when you switch your build target to other platforms.</span></span>  <span data-ttu-id="d6bf8-127">Durch die Stabilität und Erweiterbarkeit des modularen Aufbaus gibt Ihren Apps die Möglichkeit, Unterstützung für mehrere Plattformen zu bieten, wie etwa ARCore, ARKit und OpenVR.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-127">The robustness and extensibility of the modular design sets your apps up to support multiple platforms, such as ARCore, ARKit, and OpenVR.</span></span>

### <a name="performant"></a><span data-ttu-id="d6bf8-128">Leistungsfähig</span><span class="sxs-lookup"><span data-stu-id="d6bf8-128">Performant</span></span>

<span data-ttu-id="d6bf8-129">Für das Arbeiten mit mobilen Plattformen haben wir das Toolkit mit dem Augenmerk auf Leistung aufgebaut.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-129">Working with mobile platforms, we constructed it with performance in mind.</span></span>  <span data-ttu-id="d6bf8-130">Das ist äußerst wichtig, und wir wollten sicherstellen, dass die Tools sich Ihnen nicht in den Weg stellen.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-130">This is super important, and we wanted to ensure that the tools aren't going to work against you.</span></span>

## <a name="see-also"></a><span data-ttu-id="d6bf8-131">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="d6bf8-131">See also</span></span>

* [<span data-ttu-id="d6bf8-132">Installieren der Tools</span><span class="sxs-lookup"><span data-stu-id="d6bf8-132">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="d6bf8-133">Entwickeln mit MRTK für Unity</span><span class="sxs-lookup"><span data-stu-id="d6bf8-133">Developing with MRTK for Unity</span></span>](unity-development-overview.md)
* [<span data-ttu-id="d6bf8-134">MRTK – Installationshandbuch (GitHub)</span><span class="sxs-lookup"><span data-stu-id="d6bf8-134">MRTK - Installation guide (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)
* [<span data-ttu-id="d6bf8-135">Startseite der MRTK-Dokumentation (GitHub)</span><span class="sxs-lookup"><span data-stu-id="d6bf8-135">MRTK - Documentation home (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="d6bf8-136">Portieren von HoloToolkit/MRTK zu MRTK, Version 2 (GitHub)</span><span class="sxs-lookup"><span data-stu-id="d6bf8-136">Porting from HoloToolkit/MRTK to MRTK version 2 (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
