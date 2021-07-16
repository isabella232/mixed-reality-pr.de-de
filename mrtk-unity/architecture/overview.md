---
title: Übersicht über die Architektur
description: Übersicht über die Architektur des MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity,HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK-Architektur,
ms.openlocfilehash: 431e091cb6dc0efa0f941b95f58811d57166c82f
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281911"
---
# <a name="architecture-overview"></a><span data-ttu-id="c704b-104">Übersicht über die Architektur</span><span class="sxs-lookup"><span data-stu-id="c704b-104">Architecture overview</span></span>

<span data-ttu-id="c704b-105">Für eine allgemeine Einführung in den Inhalt des MRTK helfen Ihnen die in diesem Dokument enthaltenen Architekturinformationen dabei, Folgendes zu verstehen:</span><span class="sxs-lookup"><span data-stu-id="c704b-105">For an overall introduction to the contents of MRTK, the architecture information contained in this document will help you understand the following:</span></span>

- <span data-ttu-id="c704b-106">Große Teile des MRTK und wie sie eine Verbindung herstellen</span><span class="sxs-lookup"><span data-stu-id="c704b-106">Large pieces of MRTK and how they connect</span></span>
- <span data-ttu-id="c704b-107">Konzepte, die MRTK ein einführen kann, die in Unity möglicherweise nicht vorhanden sind</span><span class="sxs-lookup"><span data-stu-id="c704b-107">Concepts that MRTK introduces which may not exist in vanilla Unity</span></span>
- <span data-ttu-id="c704b-108">Funktionsweise einiger größerer Systeme (z. B. Eingabe)</span><span class="sxs-lookup"><span data-stu-id="c704b-108">How some of the larger systems (such as Input) work</span></span>

<span data-ttu-id="c704b-109">Dieser Abschnitt soll Ihnen nicht vermitteln, wie Sie Aufgaben ausführen, sondern wie diese Aufgaben strukturiert sind und warum.</span><span class="sxs-lookup"><span data-stu-id="c704b-109">This section isn't intended to teach you how to do tasks, but rather how such tasks are structured and why.</span></span>

## <a name="many-audiences-one-toolkit"></a><span data-ttu-id="c704b-110">Viele Zielgruppen, ein Toolkit</span><span class="sxs-lookup"><span data-stu-id="c704b-110">Many audiences, one toolkit</span></span>

<span data-ttu-id="c704b-111">MRTK hat keine einzelne, einheitliche Zielgruppe.</span><span class="sxs-lookup"><span data-stu-id="c704b-111">MRTK doesn't have a single, uniform audience.</span></span> <span data-ttu-id="c704b-112">Es wurde geschrieben, um Anwendungsfälle zu unterstützen, die von erstmaligen Hackathons bis hin zu Personen reichen, die komplexe, gemeinsame Erfahrungen für Unternehmen erstellen.</span><span class="sxs-lookup"><span data-stu-id="c704b-112">It's been written to support use cases ranging from first time hackathons, to individuals building complex, shared experiences for enterprise.</span></span> <span data-ttu-id="c704b-113">Möglicherweise wurden Code und APIs geschrieben, die für einen mehr als den anderen optimiert sind (d. h., einige Teile des MRTK scheinen besser für "1-Klick-Konfiguration" optimiert zu sein), aber es ist wichtig zu beachten, dass einige davon eher aus historischen gründen oder aus Gründen der Resourcing verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="c704b-113">Some code and APIs may have been written that are optimized for one more than the other (i.e. some parts of the MRTK seem more optimized for "one click configure"), but it's important to note that some of those are more for historical and resourcing reasons.</span></span> <span data-ttu-id="c704b-114">Mit der Weiterentwicklung des MRTK sollten die features, die erstellt werden, so skaliert werden, dass sie die Bandbreite von Anwendungsfällen unterstützen.</span><span class="sxs-lookup"><span data-stu-id="c704b-114">As MRTK evolves, the features that get built should be designed to scale to support the range of use cases.</span></span>

<span data-ttu-id="c704b-115">MRTK verfügt auch über Anforderungen für eine ordnungsgemäß skalieren vr- und AR-Umgebung.</span><span class="sxs-lookup"><span data-stu-id="c704b-115">MRTK also has requirements to gracefully scale across VR and AR experiences.</span></span> <span data-ttu-id="c704b-116">Es sollte einfach sein, Anwendungen zu erstellen, die bei der Bereitstellung auf einer HoloLens 2 oder einer HoloLens 1 ordnungsgemäß ein Fallback im Verhalten ermöglichen, und es sollte einfach sein, Anwendungen für OpenVR und WMR (und andere Plattformen) zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="c704b-116">It should be easy to build applications that gracefully fallback in behavior when deployed on a HoloLens 2 OR a HoloLens 1, and it should be simple to build applications that target OpenVR and WMR (and other platforms).</span></span> <span data-ttu-id="c704b-117">Manchmal kann sich das Team auf eine bestimmte Iteration auf ein bestimmtes System oder eine bestimmte Plattform konzentrieren, aber das langfristige Ziel besteht im Aufbau eines breiten Spektrums an Unterstützung für den Ort, an dem Menschen Mixed Reality-Erfahrungen erstellen.</span><span class="sxs-lookup"><span data-stu-id="c704b-117">While at times the team may focus a particular iteration on a specific system or platform, the long term goal is to build a wide range of support for wherever people are building mixed reality experiences.</span></span>

## <a name="high-level-breakdown"></a><span data-ttu-id="c704b-118">Aufschlüsselung auf hoher Ebene</span><span class="sxs-lookup"><span data-stu-id="c704b-118">High level breakdown</span></span>

<span data-ttu-id="c704b-119">Das MRTK ist sowohl eine Sammlung von Tools, um Mixed Reality-Erfahrungen (MR) schnell in die Praxis zu bringen, als auch ein Anwendungsframework mit Ansichten zur eigenen Laufzeit, wie es erweitert werden sollte und wie es konfiguriert werden sollte.</span><span class="sxs-lookup"><span data-stu-id="c704b-119">The MRTK is both a collection of tools for getting mixed reality (MR) experiences off the ground quickly, and also an application framework with opinions on its own runtime, how it should be extended, and how it should be configured.</span></span>

<span data-ttu-id="c704b-120">Auf hoher Ebene kann das MRTK wie folgt aufgeschlüsselt werden:</span><span class="sxs-lookup"><span data-stu-id="c704b-120">At a high level, the MRTK can be broken down in the following ways:</span></span>

![Übersichtsdiagramm zur Architektur](../features/images/architecture/MRTK_Architecture.png)

<span data-ttu-id="c704b-122">Das MRTK enthält auch einen weiteren Satz von Greifschnabel-Hilfsprogrammen, die nur wenig bis gar keine Abhängigkeiten vom Rest des MRTK aufweisen (um einige auflisten zu können: Buildtools, Solver, Audioeinflusser, Glättungs-Hilfsprogramme und Linienrenderer).</span><span class="sxs-lookup"><span data-stu-id="c704b-122">The MRTK also contains another set of grab-bag utilities that have little to no dependencies on the rest of the MRTK (to list a few: build tools, solvers, audio influencers, smoothing utilities, and line renderers)</span></span>

<span data-ttu-id="c704b-123">Der Rest der Architekturdokumentation wird von unten nach oben erstellt, beginnend mit dem Framework und der Runtime, und es wird zu interessanteren und komplexeren Systemen, z. B. Eingaben, entwickelt.</span><span class="sxs-lookup"><span data-stu-id="c704b-123">The remainder of the architecture documentation will build bottom up, starting from the framework and runtime, progressing to more interesting and complex systems, such as input.</span></span> <span data-ttu-id="c704b-124">Lesen Sie das Inhaltsverzeichnis, um mit der Architekturübersicht fortzufahren.</span><span class="sxs-lookup"><span data-stu-id="c704b-124">Please see the table of contents to continue with the architectural overview.</span></span>
