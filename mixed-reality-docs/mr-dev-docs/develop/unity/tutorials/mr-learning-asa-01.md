---
title: 'Tutorials zu Azure Spatial Anchors: 1 Einführung in die Tutorials zu Azure Spatial Anchors'
description: In diesem Kurs erfahren Sie, wie Sie Azure Spatial Anchors in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: fcea8bd02c81437dd7337ee94838f44f299f1927
ms.sourcegitcommit: 63c228af55379810ab2ee4f09f20eded1bb76229
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2020
ms.locfileid: "93353398"
---
# <a name="1-introduction-to-the-azure-spatial-anchors-tutorials"></a><span data-ttu-id="1522b-105">1. Einführung in die Tutorials zu Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="1522b-105">1. Introduction to the Azure Spatial Anchors tutorials</span></span>

## <a name="overview"></a><span data-ttu-id="1522b-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="1522b-106">Overview</span></span>

<span data-ttu-id="1522b-107">Willkommen bei den Tutorials zu Azure Spatial Anchors!</span><span class="sxs-lookup"><span data-stu-id="1522b-107">Welcome to the Azure Spatial Anchors tutorials!</span></span> <span data-ttu-id="1522b-108">Durch diese Tutorialreihe lernen Sie die Grundlagen von <a href="https://azure.microsoft.com/services/spatial-anchors" target="_blank">Azure Spatial Anchors</a> (ASA) kennen und erfahren, wie Sie eine vollständige Mixed Reality-Erfahrung in der realen Welt verankern.</span><span class="sxs-lookup"><span data-stu-id="1522b-108">Through this tutorial series, you will learn the fundamentals of <a href="https://azure.microsoft.com/services/spatial-anchors" target="_blank">Azure Spatial Anchors</a> (ASA) and how to anchor a complete mixed reality experience in the real world.</span></span> <span data-ttu-id="1522b-109">Außerdem erfahren Sie, wie Sie Ihr Projekt für Android und iOS bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="1522b-109">You will also learn how to deploy your project to Android and iOS.</span></span>

<span data-ttu-id="1522b-110">Tutorials in dieser Reihe:</span><span class="sxs-lookup"><span data-stu-id="1522b-110">Tutorials in this series:</span></span>

1. <span data-ttu-id="1522b-111">[Einführung](mr-learning-asa-01.md) (Sie sind bereits drin)</span><span class="sxs-lookup"><span data-stu-id="1522b-111">[Introduction](mr-learning-asa-01.md) (You're already here)</span></span>
2. [<span data-ttu-id="1522b-112">Erste Schritte mit Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="1522b-112">Getting started with Azure Spatial Anchors</span></span>](mr-learning-asa-02.md)
3. [<span data-ttu-id="1522b-113">Speichern, Abrufen und Freigeben von Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="1522b-113">Saving, retrieving, and sharing Azure Spatial Anchors</span></span>](mr-learning-asa-03.md)
4. [<span data-ttu-id="1522b-114">Anzeigen von Azure Spatial Anchors-Feedback</span><span class="sxs-lookup"><span data-stu-id="1522b-114">Displaying Azure Spatial Anchor feedback</span></span>](mr-learning-asa-04.md)
5. [<span data-ttu-id="1522b-115">Azure Spatial Anchors für Android und iOS</span><span class="sxs-lookup"><span data-stu-id="1522b-115">Azure Spatial Anchors for Android and iOS</span></span>](mr-learning-asa-05.md)

## <a name="objectives"></a><span data-ttu-id="1522b-116">Ziele</span><span class="sxs-lookup"><span data-stu-id="1522b-116">Objectives</span></span>

* <span data-ttu-id="1522b-117">Erfahren, wie Raumanker erstellt und aus Azure abgerufen werden</span><span class="sxs-lookup"><span data-stu-id="1522b-117">Learn how to create spatial anchors and fetch them from Azure</span></span>
* <span data-ttu-id="1522b-118">Erfahren, wie die räumliche Ausrichtung über mehrere App-Sitzungen erreicht wird</span><span class="sxs-lookup"><span data-stu-id="1522b-118">Learn how to achieve spatial alignment across app sessions</span></span>
* <span data-ttu-id="1522b-119">Erfahren, wie räumliche Ausrichtung zwischen mehreren Geräten erreicht werden kann</span><span class="sxs-lookup"><span data-stu-id="1522b-119">Learn how to achieve spatial alignment between multiple devices</span></span>
* <span data-ttu-id="1522b-120">Erfahren, wie Ihr Projekt für Android und iOS vorbereitet, erstellt und bereitgestellt wird</span><span class="sxs-lookup"><span data-stu-id="1522b-120">Learn how to prepare, build, and deploy your project to Android and iOS</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1522b-121">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="1522b-121">Prerequisites</span></span>

* <span data-ttu-id="1522b-122">Ein Windows 10-Computer, auf dem die richtigen [Tools installiert](../../install-the-tools.md) sind</span><span class="sxs-lookup"><span data-stu-id="1522b-122">A Windows 10 computer configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="1522b-123">Windows 10 SDK (Version 10.0.18362.0 oder höher)</span><span class="sxs-lookup"><span data-stu-id="1522b-123">Windows 10 SDK 10.0.18362.0 or later version</span></span>
* <span data-ttu-id="1522b-124">Ein für die [Entwicklung konfiguriertes](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) HoloLens 2-Gerät</span><span class="sxs-lookup"><span data-stu-id="1522b-124">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="1522b-125"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> mit installiertem Unity 2019.3.15 und hinzugefügtem Buildunterstützungsmodul für die Universelle Windows-Plattform</span><span class="sxs-lookup"><span data-stu-id="1522b-125"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="1522b-126">Durchgearbeiteter Abschnitt [Erstellen einer Spatial Anchors-Ressource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) des Tutorials [Schnellstart: Erstellen einer Unity HoloLens-App, die Azure Spatial Anchors verwendet](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens)</span><span class="sxs-lookup"><span data-stu-id="1522b-126">Completed the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial</span></span>
* <span data-ttu-id="1522b-127">Durchgearbeitete Tutorialreihe [Erste Schritte](mr-learning-base-01.md) oder vorherige grundlegende Erfahrung mit Unity und MRTK</span><span class="sxs-lookup"><span data-stu-id="1522b-127">Finished the [Getting started tutorials](mr-learning-base-01.md) series or some basic prior experience with Unity and MRTK</span></span>
* <span data-ttu-id="1522b-128">Wenn Sie unter Android sowie HoloLens bereitstellen möchten</span><span class="sxs-lookup"><span data-stu-id="1522b-128">If you intend to deploy to Android as well as HoloLens</span></span>
  * <span data-ttu-id="1522b-129">Ein Android-Gerät mit <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">Entwicklerunterstützung</a> und <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore-Unterstützung</a> mit USB-Verbindung zu Ihrem Windows- oder macOS-Computer</span><span class="sxs-lookup"><span data-stu-id="1522b-129">A <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">developer enabled</a> and <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore capable</a> Android device with USB connection to your Windows or macOS computer</span></span>
  * <span data-ttu-id="1522b-130"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> mit installiertem Unity 2019.3.15 und hinzugefügtem Buildunterstützungsmodul für Android</span><span class="sxs-lookup"><span data-stu-id="1522b-130"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the Android Build Support module added</span></span>
* <span data-ttu-id="1522b-131">Wenn Sie unter iOS sowie HoloLens bereitstellen möchten</span><span class="sxs-lookup"><span data-stu-id="1522b-131">If you intend to deploy to iOS as well as HoloLens</span></span>
  * <span data-ttu-id="1522b-132">Ein macOS-Computer mit installierter neuester Version von <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> und <a href="https://cocoapods.org" target="_blank">CocoaPods</a></span><span class="sxs-lookup"><span data-stu-id="1522b-132">A macOS computer with the latest version of <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> and <a href="https://cocoapods.org" target="_blank">CocoaPods</a> installed</span></span>
  * <span data-ttu-id="1522b-133">Ein iOS-Gerät mit <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit-Unterstützung</a> und USB-Verbindung mit Ihrem macOS-Computer</span><span class="sxs-lookup"><span data-stu-id="1522b-133">An <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit compatible</a> iOS device with USB connection to your macOS computer</span></span>
  * <span data-ttu-id="1522b-134"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> mit installiertem Unity 2019.3.15 und hinzugefügtem Buildunterstützungsmodul für iOS</span><span class="sxs-lookup"><span data-stu-id="1522b-134"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the iOS Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="1522b-135">Die empfohlene Mixed Reality Toolkit-Version für diese Tutorialreihe ist MRTK 2.4.0.</span><span class="sxs-lookup"><span data-stu-id="1522b-135">The recommended Mixed Reality Toolkit version for this tutorial series is MRTK 2.4.0.</span></span>

> [!CAUTION]
> <span data-ttu-id="1522b-136">Die empfohlene Unity-Version für diese Tutorialreihe ist Unity 2019.3.15.</span><span class="sxs-lookup"><span data-stu-id="1522b-136">The recommended Unity version for this tutorial series is Unity 2019.3.15.</span></span> <span data-ttu-id="1522b-137">Diese Informationen besitzen Vorrang vor allen Unity-Versionsanforderungen, die in den oben verlinkten Voraussetzungen angegeben sind.</span><span class="sxs-lookup"><span data-stu-id="1522b-137">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1522b-138">Nächstes Tutorial: 2. Erste Schritte mit Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="1522b-138">Next Tutorial: 2. Getting started with Azure Spatial Anchors</span></span>](mr-learning-asa-02.md)
