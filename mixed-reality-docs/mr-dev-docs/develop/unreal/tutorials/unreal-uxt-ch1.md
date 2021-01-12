---
title: 1. Erste Schritte
description: Teil 1 von 6 einer Tutorialreihe zum Erstellen einer Schach-App mit der Unreal Engine 4 und dem UX Tools-Plug-In des Mixed Reality-Toolkits
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Tutorial, Erste Schritte, MRTK, UXT, UX-Tools, Dokumentation, Mixed Reality-Headset Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 762247f550a3471bbbb6d1004283c6f901346503
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009790"
---
# <a name="1-getting-started"></a><span data-ttu-id="254db-104">1. Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="254db-104">1. Getting started</span></span>

<span data-ttu-id="254db-105">Einsteigern in die Welt der Mixed Reality ebenso wie erfahrenen Experten wird hier gleichermaßen der ideale Ausgangspunkt geboten, um ihre [HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/)- und [Unreal Engine](https://www.unrealengine.com/en-US/)-Journey zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="254db-105">Whether you're new to mixed reality or a seasoned pro, you're in the right place to start your [HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/) and [Unreal Engine](https://www.unrealengine.com/en-US/) journey.</span></span> <span data-ttu-id="254db-106">In dieser Tutorialreihe erhalten Sie eine ausführliche Anleitung zum Erstellen einer interaktiven Schach-App mit dem [UX Tools-Plug-In](https://github.com/microsoft/MixedReality-UXTools-Unreal), das Teil des [Mixed Reality Toolkit für Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal) ist.</span><span class="sxs-lookup"><span data-stu-id="254db-106">This tutorial series will give you a step-by-step guide on how to build an interactive chess app with the [UX Tools plugin](https://github.com/microsoft/MixedReality-UXTools-Unreal) - part of the [Mixed Reality Toolkit for Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal).</span></span> <span data-ttu-id="254db-107">Das Plug-in unterstützt Sie beim Hinzufügen allgemeiner UX-Features zu Ihren Projekten anhand von Code, Blaupausen und Beispielen.</span><span class="sxs-lookup"><span data-stu-id="254db-107">The plugin will help you add common UX features to your projects with code, blueprints, and examples.</span></span> 

![Fertige Szene im Viewport](images/unreal-uxt/5-endscene.PNG)

<span data-ttu-id="254db-109">Am Ende der Reihe haben Sie Erfahrungen mit folgenden Aufgaben gesammelt:</span><span class="sxs-lookup"><span data-stu-id="254db-109">By the end of the series you'll have experience with:</span></span>
* <span data-ttu-id="254db-110">Erstellen eines neuen Projekts</span><span class="sxs-lookup"><span data-stu-id="254db-110">Starting a new project</span></span>
* <span data-ttu-id="254db-111">Einrichtung für Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="254db-111">Setting up for mixed reality</span></span>
* <span data-ttu-id="254db-112">Arbeiten mit Benutzereingaben</span><span class="sxs-lookup"><span data-stu-id="254db-112">Working with user input</span></span>
* <span data-ttu-id="254db-113">Hinzufügen von Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="254db-113">Adding buttons</span></span>
* <span data-ttu-id="254db-114">Wiedergabe in einem Emulator oder auf einem Gerät</span><span class="sxs-lookup"><span data-stu-id="254db-114">Playing on an emulator or device</span></span>

## <a name="prerequisites"></a><span data-ttu-id="254db-115">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="254db-115">Prerequisites</span></span>

<span data-ttu-id="254db-116">Achten Sie darauf, dass Sie die folgenden Produkte installiert haben, bevor Sie einsteigen:</span><span class="sxs-lookup"><span data-stu-id="254db-116">Make sure you've installed the following before jumping in:</span></span>
* <span data-ttu-id="254db-117">Windows 10 (1809 oder höher)</span><span class="sxs-lookup"><span data-stu-id="254db-117">Windows 10 1809 or later</span></span>
* <span data-ttu-id="254db-118">Windows 10 SDK (10.0.18362.0 oder höher)</span><span class="sxs-lookup"><span data-stu-id="254db-118">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="254db-119">[Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.25 oder höher</span><span class="sxs-lookup"><span data-stu-id="254db-119">[Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.25 or later</span></span>
* <span data-ttu-id="254db-120">[Für die Entwicklung](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) oder einen [Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-2-emulator-overview) konfiguriertes Microsoft HoloLens 2-Gerät</span><span class="sxs-lookup"><span data-stu-id="254db-120">Microsoft HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) or [Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-2-emulator-overview)</span></span>
* <span data-ttu-id="254db-121">Visual Studio 2019 mit den folgenden Workloads</span><span class="sxs-lookup"><span data-stu-id="254db-121">Visual Studio 2019 with the workloads below</span></span>

### <a name="installing-visual-studio-2019"></a><span data-ttu-id="254db-122">Installieren von Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="254db-122">Installing Visual Studio 2019</span></span>

<span data-ttu-id="254db-123">Stellen Sie zunächst sicher, dass Ihre Einrichtung über alle erforderlichen Visual Studio-Pakete verfügt:</span><span class="sxs-lookup"><span data-stu-id="254db-123">First, make sure your setup with all the required Visual Studio packages:</span></span>
1. <span data-ttu-id="254db-124">Installieren Sie die aktuelle Version von [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/).</span><span class="sxs-lookup"><span data-stu-id="254db-124">Install the latest version of [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/)</span></span>
1. <span data-ttu-id="254db-125">Installieren Sie die folgenden [Workloads](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?#modify-workloads):</span><span class="sxs-lookup"><span data-stu-id="254db-125">Install the following [workloads](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?#modify-workloads):</span></span>
    * <span data-ttu-id="254db-126">Desktopentwicklung mit C++</span><span class="sxs-lookup"><span data-stu-id="254db-126">Desktop development with C++</span></span>
    * <span data-ttu-id="254db-127">.NET-Desktopentwicklung</span><span class="sxs-lookup"><span data-stu-id="254db-127">.NET desktop development</span></span>
    * <span data-ttu-id="254db-128">Entwicklung für die universelle Windows-Plattform</span><span class="sxs-lookup"><span data-stu-id="254db-128">Universal Windows Platform development</span></span>
1. <span data-ttu-id="254db-129">Klappen Sie die Entwicklung für die Universelle Windows-Plattform auf, und wählen Sie Folgendes aus:</span><span class="sxs-lookup"><span data-stu-id="254db-129">Expand Universal Windows Platform development and select:</span></span> 
    * <span data-ttu-id="254db-130">USB-Gerätekonnektivität</span><span class="sxs-lookup"><span data-stu-id="254db-130">USB Device Connectivity</span></span>
    * <span data-ttu-id="254db-131">UWP-Tools (Universelle Windows-Plattform) für C++ (v142)</span><span class="sxs-lookup"><span data-stu-id="254db-131">C++ (v142) Universal Windows Platform tools</span></span>

1. <span data-ttu-id="254db-132">Installieren Sie die folgenden [Komponenten](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?#modify-individual-components):</span><span class="sxs-lookup"><span data-stu-id="254db-132">Install the following [components](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?#modify-individual-components):</span></span>
    * <span data-ttu-id="254db-133">„Compiler, Buildtools und Runtimes“ > „MSVC v142 – VS 2019 C++-ARM64-Buildtools“ (neueste Version)</span><span class="sxs-lookup"><span data-stu-id="254db-133">Compilers, build tools, and runtimes > MSVC v142 - VS 2019 C++ ARM64 build tools (latest version)</span></span>

<span data-ttu-id="254db-134">Sie können die Installation mit der folgenden Abbildung bestätigen</span><span class="sxs-lookup"><span data-stu-id="254db-134">You can confirm the installation with the following picture</span></span>

![Wichtige Optionen im VS-Installationsprogramm](images/unreal-uxt/1-install-the-tools.png)

<span data-ttu-id="254db-136">Das war's.</span><span class="sxs-lookup"><span data-stu-id="254db-136">That's it!</span></span> <span data-ttu-id="254db-137">Jetzt haben Sie alle Vorbereitungen getroffen, um mit dem Schach-Projekt beginnen zu können.</span><span class="sxs-lookup"><span data-stu-id="254db-137">You're all set to move on to starting the chess project.</span></span>

[<span data-ttu-id="254db-138">Nächster Abschnitt: 2. Initialisieren des Projekts und der ersten Anwendung</span><span class="sxs-lookup"><span data-stu-id="254db-138">Next section: 2. Initializing your project and first application</span></span>](unreal-uxt-ch2.md)