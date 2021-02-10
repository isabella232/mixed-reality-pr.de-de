---
title: Einführung in die Tutorials zu Mehrbenutzerfunktionen
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie freigegebene Mehrbenutzerumgebungen in einer HoloLens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, Mehrbenutzerfunktionen, Photon, MRTK, Mixed Reality Toolkit, UWP, Azure Spatial Anchors
ms.localizationpriority: high
ms.openlocfilehash: 90c5b2ee3f25c39fc644aee0fbbf49643f7d2a59
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590172"
---
# <a name="1-introduction-to-the-multi-user-capabilities-tutorials"></a><span data-ttu-id="c6bf2-104">1. Einführung in die Tutorials zu Mehrbenutzerfunktionen</span><span class="sxs-lookup"><span data-stu-id="c6bf2-104">1. Introduction to the Multi-user capabilities tutorials</span></span>

<span data-ttu-id="c6bf2-105">Willkommen bei den Tutorials zu Mehrbenutzerfunktionen!</span><span class="sxs-lookup"><span data-stu-id="c6bf2-105">Welcome to the Multi-User Capabilities tutorials!</span></span> <span data-ttu-id="c6bf2-106">In dieser Tutorialreihe erlernen Sie die Grundlagen zum Entwickeln einer Mehrbenutzerumgebung mithilfe von <a href="https://www.photonengine.com/PUN" target="_blank">Photon Unity Networking</a> (PUN).</span><span class="sxs-lookup"><span data-stu-id="c6bf2-106">Through this tutorial series, you will learn the fundamentals of building a multi-user experience using <a href="https://www.photonengine.com/PUN" target="_blank">Photon Unity Networking</a> (PUN).</span></span> <span data-ttu-id="c6bf2-107">PUN ist eine von mehreren Netzwerkoptionen, die Mixed Reality-Entwicklern zum Erstellen gemeinsamer Benutzererfahrungen zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="c6bf2-107">PUN is one of several networking options available to mixed reality developers to create shared experiences.</span></span>

<span data-ttu-id="c6bf2-108">Tutorials in dieser Reihe:</span><span class="sxs-lookup"><span data-stu-id="c6bf2-108">Tutorials in this series:</span></span>

* [<span data-ttu-id="c6bf2-109">Einrichten von Photon Unity Networking</span><span class="sxs-lookup"><span data-stu-id="c6bf2-109">Setting up Photon Unity Networking</span></span>](mr-learning-sharing-02.md)
* [<span data-ttu-id="c6bf2-110">Verbinden mehrerer Benutzer</span><span class="sxs-lookup"><span data-stu-id="c6bf2-110">Connecting multiple users</span></span>](mr-learning-sharing-03.md)
* [<span data-ttu-id="c6bf2-111">Freigeben von Objektbewegungen für mehrere Benutzer</span><span class="sxs-lookup"><span data-stu-id="c6bf2-111">Sharing object movements with multiple users</span></span>](mr-learning-sharing-04.md)
* [<span data-ttu-id="c6bf2-112">Integrieren von Azure Spatial Anchors in eine gemeinsam genutzte Umgebung</span><span class="sxs-lookup"><span data-stu-id="c6bf2-112">Integrating Azure Spatial Anchors into a shared experience</span></span>](mr-learning-sharing-05.md)

## <a name="objectives"></a><span data-ttu-id="c6bf2-113">Ziele</span><span class="sxs-lookup"><span data-stu-id="c6bf2-113">Objectives</span></span>

* <span data-ttu-id="c6bf2-114">Erfahren, wie PUN-App erstellt und eine Verbindung Ihres Unity-Projekts mit ihr hergestellt wird</span><span class="sxs-lookup"><span data-stu-id="c6bf2-114">Learn how to create a PUN app and connect your Unity project to it</span></span>
* <span data-ttu-id="c6bf2-115">Erlernen des Verbindens mehrerer Benutzer in einer freigegebenen Umgebung</span><span class="sxs-lookup"><span data-stu-id="c6bf2-115">Learn how to connect multiple users in a shared experience</span></span>
* <span data-ttu-id="c6bf2-116">Erfahren, wie Objektbewegungen mit anderen Benutzern geteilt werden können</span><span class="sxs-lookup"><span data-stu-id="c6bf2-116">Learn how to share the object movements with other users</span></span>
* <span data-ttu-id="c6bf2-117">Erfahren, wie räumliche Ausrichtung zwischen mehreren Geräten erreicht werden kann</span><span class="sxs-lookup"><span data-stu-id="c6bf2-117">Learn how to achieve spatial alignment between multiple devices</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c6bf2-118">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="c6bf2-118">Prerequisites</span></span>

* <span data-ttu-id="c6bf2-119">Ein Windows 10-Computer, auf dem die richtigen [Tools installiert](../../install-the-tools.md) sind</span><span class="sxs-lookup"><span data-stu-id="c6bf2-119">A Windows 10 computer configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="c6bf2-120">Windows 10 SDK (10.0.18362.0 oder höher)</span><span class="sxs-lookup"><span data-stu-id="c6bf2-120">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="c6bf2-121">Ein für die [Entwicklung konfiguriertes](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) HoloLens 2-Gerät</span><span class="sxs-lookup"><span data-stu-id="c6bf2-121">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="c6bf2-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> mit installiertem Unity 2019 LTS und hinzugefügtem Buildunterstützungsmodul für die Universelle Windows-Plattform</span><span class="sxs-lookup"><span data-stu-id="c6bf2-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="c6bf2-123">Durchgearbeiteter Abschnitt [Erstellen einer Spatial Anchors-Ressource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) des Tutorials [Schnellstart: Erstellen einer Unity HoloLens-App, die Azure Spatial Anchors verwendet](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens).</span><span class="sxs-lookup"><span data-stu-id="c6bf2-123">Completed the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial</span></span>
* <span data-ttu-id="c6bf2-124">Durchgearbeitete Tutorialserie [Erste Schritte](mr-learning-base-01.md) oder vorherige grundlegende Erfahrung mit Unity und MRTK</span><span class="sxs-lookup"><span data-stu-id="c6bf2-124">Completed the [Getting started tutorials](mr-learning-base-01.md) series or some basic prior experience with Unity and MRTK</span></span>
* <span data-ttu-id="c6bf2-125">Durchgearbeitete [Tutorialserie „Azure Spatial Anchors“](mr-learning-asa-01.md) oder vorherige Erfahrung im Erstellen eines Azure Spatial Anchors-Kontos</span><span class="sxs-lookup"><span data-stu-id="c6bf2-125">Completed the [Azure Spatial Anchors tutorials](mr-learning-asa-01.md) series or prior experience creating an Azure Spatial Anchors Account</span></span>
* <span data-ttu-id="c6bf2-126">Wenn Sie unter Android sowie HoloLens bereitstellen möchten</span><span class="sxs-lookup"><span data-stu-id="c6bf2-126">If you intend to deploy to Android as well as HoloLens</span></span>
  * <span data-ttu-id="c6bf2-127">Ein Android-Gerät mit <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">Entwicklerunterstützung</a> und <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore-Unterstützung</a> mit USB-Verbindung zu Ihrem Windows- oder macOS-Computer</span><span class="sxs-lookup"><span data-stu-id="c6bf2-127">A <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">developer enabled</a> and <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore capable</a> Android device with USB connection to your Windows or macOS computer</span></span>
  * <span data-ttu-id="c6bf2-128"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> mit installiertem Unity 2019 LTS und hinzugefügtem Buildunterstützungsmodul für Android</span><span class="sxs-lookup"><span data-stu-id="c6bf2-128"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS installed and the Android Build Support module added</span></span>
* <span data-ttu-id="c6bf2-129">Wenn Sie unter iOS sowie HoloLens bereitstellen möchten</span><span class="sxs-lookup"><span data-stu-id="c6bf2-129">If you intend to deploy to iOS as well as HoloLens</span></span>
  * <span data-ttu-id="c6bf2-130">Ein macOS-Computer mit installierter neuester Version von <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> und <a href="https://cocoapods.org" target="_blank">CocoaPods</a></span><span class="sxs-lookup"><span data-stu-id="c6bf2-130">A macOS computer with the latest version of <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> and <a href="https://cocoapods.org" target="_blank">CocoaPods</a> installed</span></span>
  * <span data-ttu-id="c6bf2-131">Ein iOS-Gerät mit <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit-Unterstützung</a> und USB-Verbindung mit Ihrem macOS-Computer</span><span class="sxs-lookup"><span data-stu-id="c6bf2-131">An <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit compatible</a> iOS device with USB connection to your macOS computer</span></span>
  * <span data-ttu-id="c6bf2-132"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> mit installiertem Unity 2019 LTS und hinzugefügtem Buildunterstützungsmodul für iOS</span><span class="sxs-lookup"><span data-stu-id="c6bf2-132"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS installed and the iOS Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="c6bf2-133">Die empfohlene Mixed Reality Toolkit-Version für diese Tutorialreihe ist MRTK 2.5.3.</span><span class="sxs-lookup"><span data-stu-id="c6bf2-133">The recommended Mixed Reality Toolkit version for this tutorial series is MRTK 2.5.3.</span></span>

> [!CAUTION]
> <span data-ttu-id="c6bf2-134">Die empfohlene Unity-Version für diese Tutorialreihe ist Unity 2019 LTS. Diese ersetzt alle Unity-Versionsanforderungen, die in den oben verlinkten Voraussetzungen angegeben sind.</span><span class="sxs-lookup"><span data-stu-id="c6bf2-134">The recommended Unity version for this tutorial series is Unity 2019 LTS This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c6bf2-135">Nächstes Tutorial: 2. Einrichten von Photon Unity Networking</span><span class="sxs-lookup"><span data-stu-id="c6bf2-135">Next Tutorial: 2. Setting up Photon Unity Networking</span></span>](mr-learning-sharing-02.md)
