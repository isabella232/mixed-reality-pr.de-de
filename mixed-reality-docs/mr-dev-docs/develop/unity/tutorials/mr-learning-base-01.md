---
title: Einführung in die MRTK-Tutorials
description: In diesem Kurs erfahren Sie, wie Sie das Mixed Reality Toolkit (MRTK) verwenden, um eine Mixed Reality-Anwendung von Grund auf zu erstellen.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, MRTK, Mixed Reality Toolkit, Solver, Eye Tracking, Sprachbefehle
ms.localizationpriority: high
ms.openlocfilehash: a917aea812c262e3589110a29e2399da4c1e5348
ms.sourcegitcommit: a56a551ebc59529a3683fe6db90d59f982ab0b45
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/19/2021
ms.locfileid: "98579269"
---
# <a name="1-introduction-to-the-mrtk-tutorials"></a><span data-ttu-id="22880-104">1. Einführung in die MRTK-Tutorials</span><span class="sxs-lookup"><span data-stu-id="22880-104">1. Introduction to the MRTK tutorials</span></span>

<span data-ttu-id="22880-105">Willkommen bei der Tutorialreihe zu den ersten Schritten!</span><span class="sxs-lookup"><span data-stu-id="22880-105">Welcome to the Getting Started tutorial series!</span></span> <span data-ttu-id="22880-106">Im Verlauf dieser Tutorials lernen Sie das Mixed Reality Toolkit (MRTK) und einige der von ihm gebotenen Features kennen.</span><span class="sxs-lookup"><span data-stu-id="22880-106">Over the course of these tutorials, you'll learn about the Mixed Reality Toolkit (MRTK) and some of the features it has to offer.</span></span> <span data-ttu-id="22880-107">Sie erstellen außerdem ein Mixed Reality-Erlebnis, in dem der Benutzer ein Hologramm erforschen kann, das eine Nachbildung des Curiosity-Mars-Rovers der NASA darstellt.</span><span class="sxs-lookup"><span data-stu-id="22880-107">You'll also build a mixed reality experience where the user can explore a hologram modeled after NASA's Mars Curiosity Rover.</span></span> <span data-ttu-id="22880-108">Am Ende dieser Reihe haben Sie ein sicheres Verständnis des MRTK und der Weise, in der es Ihren Entwicklungsprozess beschleunigen kann.</span><span class="sxs-lookup"><span data-stu-id="22880-108">By the end of this series, you'll have a firm grasp of MRTK and how it can speed up your development process.</span></span>

<span data-ttu-id="22880-109">Die Tutorials in dieser Reihe sind auf eine bestimmte Abfolge ausgelegt, also arbeiten Sie sie bitte in der richtigen Reihenfolge ab:</span><span class="sxs-lookup"><span data-stu-id="22880-109">Tutorials in this series are meant to be sequential, so please go through them in the correct order:</span></span>

1. <span data-ttu-id="22880-110">[Einführung](mr-learning-base-01.md) (Sie sind bereits drin)</span><span class="sxs-lookup"><span data-stu-id="22880-110">[Introduction](mr-learning-base-01.md) (You're already here)</span></span>
2. [<span data-ttu-id="22880-111">Initialisieren Ihres Projekts und Bereitstellen Ihrer ersten Anwendung</span><span class="sxs-lookup"><span data-stu-id="22880-111">Initializing your project and deploying your first application</span></span>](mr-learning-base-02.md)
3. [<span data-ttu-id="22880-112">Konfigurieren der MRTK-Profile</span><span class="sxs-lookup"><span data-stu-id="22880-112">Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
4. [<span data-ttu-id="22880-113">Positionieren von Objekten in der Szene</span><span class="sxs-lookup"><span data-stu-id="22880-113">Positioning objects in the scene</span></span>](mr-learning-base-04.md)
5. [<span data-ttu-id="22880-114">Erstellen dynamischer Inhalte mithilfe von Solvern</span><span class="sxs-lookup"><span data-stu-id="22880-114">Creating dynamic content using Solvers</span></span>](mr-learning-base-05.md)
6. [<span data-ttu-id="22880-115">Erstellen der Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="22880-115">Creating user interfaces</span></span>](mr-learning-base-06.md)
7. [<span data-ttu-id="22880-116">Interagieren mit 3D-Objekten</span><span class="sxs-lookup"><span data-stu-id="22880-116">Interacting with 3D objects</span></span>](mr-learning-base-07.md)
8. [<span data-ttu-id="22880-117">Verwenden von Eye Tracking</span><span class="sxs-lookup"><span data-stu-id="22880-117">Using eye-tracking</span></span>](mr-learning-base-08.md)
9. [<span data-ttu-id="22880-118">Verwenden von Sprachbefehlen</span><span class="sxs-lookup"><span data-stu-id="22880-118">Using voice commands</span></span>](mr-learning-base-09.md)

## <a name="objectives"></a><span data-ttu-id="22880-119">Ziele</span><span class="sxs-lookup"><span data-stu-id="22880-119">Objectives</span></span>

* <span data-ttu-id="22880-120">Erfahren, wie Unity für MRTK konfiguriert wird</span><span class="sxs-lookup"><span data-stu-id="22880-120">Learn how to configure Unity for MRTK</span></span>
* <span data-ttu-id="22880-121">Erfahren, wie Sie auf Ihrem lokalen Computer erstellen und bereitstellen</span><span class="sxs-lookup"><span data-stu-id="22880-121">Learn how to build and deploy to your device</span></span>
* <span data-ttu-id="22880-122">Erfahren, wie einige der Schlüsselfunktionen des MRTK verwendet werden</span><span class="sxs-lookup"><span data-stu-id="22880-122">Learn how to use some of MRTK's key features</span></span>
* <span data-ttu-id="22880-123">Erstellen eines umfassenden Mixed Reality-Erlebnisses</span><span class="sxs-lookup"><span data-stu-id="22880-123">Create a complete mixed reality experience</span></span>

## <a name="prerequisites"></a><span data-ttu-id="22880-124">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="22880-124">Prerequisites</span></span>

* <span data-ttu-id="22880-125">Ein Windows 10-PC, der mit den richtigen [Tools konfiguriert](../../install-the-tools.md) ist</span><span class="sxs-lookup"><span data-stu-id="22880-125">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="22880-126">[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk/) (10.0.18362.0 oder höher)</span><span class="sxs-lookup"><span data-stu-id="22880-126">[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk/) 10.0.18362.0 or later</span></span>
* <span data-ttu-id="22880-127">Ein für die [Entwicklung konfiguriertes](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) HoloLens 2-Gerät</span><span class="sxs-lookup"><span data-stu-id="22880-127">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>

* <span data-ttu-id="22880-128"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> mit installiertem Unity 2019 LTS und hinzugefügtem Buildunterstützungsmodul für die Universelle Windows-Plattform</span><span class="sxs-lookup"><span data-stu-id="22880-128"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS installed and the Universal Windows Platform Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="22880-129">Die empfohlene MRTK-Version für diese Tutorialreihe ist MRTK 2.5.1.</span><span class="sxs-lookup"><span data-stu-id="22880-129">The recommended MRTK version for this tutorial series is MRTK 2.5.1.</span></span>

> [!CAUTION]
> <span data-ttu-id="22880-130">Die empfohlene Unity-Version für diese Tutorialserie ist Unity 2019 LTS.</span><span class="sxs-lookup"><span data-stu-id="22880-130">The recommended Unity version for this tutorial series is Unity 2019 LTS.</span></span> <span data-ttu-id="22880-131">Diese Information hat Vorrang vor allen Unity-Versionsanforderungen, die in den oben verlinkten Voraussetzungen angegeben sind.</span><span class="sxs-lookup"><span data-stu-id="22880-131">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="22880-132">Nächstes Tutorial: 2. Initialisieren Ihres Projekts und Bereitstellen Ihrer ersten Anwendung</span><span class="sxs-lookup"><span data-stu-id="22880-132">Next Tutorial: 2. Initializing your project and deploying your first application</span></span>](mr-learning-base-02.md)
