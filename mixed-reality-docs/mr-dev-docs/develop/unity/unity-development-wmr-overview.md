---
title: Unity-Bereitstellung für VR
description: Beginnen Sie mit dem Entwickeln von Mixed Reality-Apps in Unity für immersive Headsets für VR und Windows Mixed Reality.
author: hferrone
ms.author: kurtie
ms.date: 12/11/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unity, Mixed Reality, Entwicklung, Erste Schritte, neues Projekt, Portieren, Funktion, Kamera, Simulation, Emulation, Dokumentation, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, was ist Virtual Reality, was ist Augmented Reality, MRTK, Mixed Reality Toolkit, Spracheingabe, ausrichtbare Kamera, Emulator, Azure, Tutorials
ms.openlocfilehash: ba63f137e90b68345f3e5bbb831aba6abd6fe538
ms.sourcegitcommit: b13c517df19179ca281362a1f006914289c58ad4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2021
ms.locfileid: "98040565"
---
# <a name="unity-development-for-vr-and-windows-mixed-reality"></a><span data-ttu-id="ffded-104">Unity-Entwicklung für VR und Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="ffded-104">Unity development for VR and Windows Mixed Reality</span></span>

![Unity-Bannerlogo](../images/unity_logo_banner.png)

<span data-ttu-id="ffded-106">Wenn Sie mit Unity noch nicht vertraut sind, empfehlen wir Ihnen, sich mit den [Tutorials](https://unity3d.com/learn/tutorials) für Einsteiger auf der Unity-Lernplattform zu befassen, bevor Sie fortfahren.</span><span class="sxs-lookup"><span data-stu-id="ffded-106">If you're brand new to Unity, we recommend that you explore the beginner level [tutorials](https://unity3d.com/learn/tutorials) on the Unity Learn platform before continuing.</span></span> <span data-ttu-id="ffded-107">Außerdem ist es eine gute Idee, die [Unity Mixed Reality-Foren](https://forum.unity3d.com/forums/hololens.102/) aufzusuchen, um sich in der Onlinecommunity zu engagieren, die Mixed Reality-Apps erstellt.</span><span class="sxs-lookup"><span data-stu-id="ffded-107">It's also a good idea to visit the [Unity Mixed Reality forums](https://forum.unity3d.com/forums/hololens.102/) to engage with the online community building mixed reality apps.</span></span> <span data-ttu-id="ffded-108">Sie können schlicht nicht wissen, welche tollen Medienobjekte oder Lösungen Sie abseits ausgetretener Pfade finden.</span><span class="sxs-lookup"><span data-stu-id="ffded-108">You never know what cool assets or solutions you might find out in the wild.</span></span> <span data-ttu-id="ffded-109">Wenn Sie bereit sind, mit dem MRTK loszulegen, gehen Sie zu den Prüfpunkten für die Entwicklung unten!</span><span class="sxs-lookup"><span data-stu-id="ffded-109">When you're ready to get started with MRTK head to the development checkpoints below!</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ffded-110">Sehen Sie sich unsere **[Portierungsleitfäden](../porting-apps/porting-overview.md)** an, wenn Sie ein vorhandenes Unity-Projekt auf ein immersives Windows Mixed Reality-Headset portieren möchten.</span><span class="sxs-lookup"><span data-stu-id="ffded-110">Take a look at our **[porting guides](../porting-apps/porting-overview.md)** if you have an existing Unity project that you want to bring over to a Windows Mixed Reality immersive headset.</span></span> 

## <a name="development-checkpoints"></a><span data-ttu-id="ffded-111">Prüfpunkte für die Entwicklung</span><span class="sxs-lookup"><span data-stu-id="ffded-111">Development checkpoints</span></span>

<span data-ttu-id="ffded-112">Nutzen Sie die folgenden Prüfpunkte, um Ihre Unity-Spiele und Anwendungen in eine Mixed Reality-Welt einzubringen.</span><span class="sxs-lookup"><span data-stu-id="ffded-112">Use the following checkpoints to bring your Unity games and applications into the world of mixed reality.</span></span> 

### <a name="1-getting-started"></a><span data-ttu-id="ffded-113">1. Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="ffded-113">1. Getting started</span></span>

<span data-ttu-id="ffded-114">Es gibt eine kleine Gruppe von Unity-Einstellungen, die Sie für die Entwicklung für Windows Mixed Reality und VR manuell ändern müssen.</span><span class="sxs-lookup"><span data-stu-id="ffded-114">There are a small set of Unity settings you'll need to manually change for Windows Mixed Reality and VR developoment.</span></span> <span data-ttu-id="ffded-115">Diese gliedern sich in zwei Kategorien: projektbezogene und szenenbezogene.</span><span class="sxs-lookup"><span data-stu-id="ffded-115">These are broken down into two categories: per-project and per-scene.</span></span> <span data-ttu-id="ffded-116">Am Ende dieses Abschnitts verfügen Sie über die Tools und Projekteinstellungen, um mit dem Erstellen Ihrer eigenen Apps zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="ffded-116">By the end of this section, you'll have the tools and project settings to start creating your own apps!</span></span>

|  <span data-ttu-id="ffded-117">Prüfpunkt</span><span class="sxs-lookup"><span data-stu-id="ffded-117">Checkpoint</span></span>  |  <span data-ttu-id="ffded-118">Ergebnis</span><span class="sxs-lookup"><span data-stu-id="ffded-118">Outcome</span></span>  |
| --- | --- |
| [<span data-ttu-id="ffded-119">Installieren der neuesten Tools</span><span class="sxs-lookup"><span data-stu-id="ffded-119">Install the latest tools</span></span>](../install-the-tools.md) | <span data-ttu-id="ffded-120">Laden Sie das aktuellste Unreal-Paket herunter, installieren Sie es, und richten Sie Ihr Projekt für Mixed Reality ein</span><span class="sxs-lookup"><span data-stu-id="ffded-120">Download and install the latest Unity package and setup your project for mixed reality</span></span> |
| [<span data-ttu-id="ffded-121">Konfigurieren Ihres Projekts für WMR</span><span class="sxs-lookup"><span data-stu-id="ffded-121">Configuring your project for WMR</span></span>](configure-unity-project.md) | <span data-ttu-id="ffded-122">Erfahren Sie, wie Sie Anwendungen erstellen, die digitale Inhalte auf holografischen und VR-Anzeigegeräten darstellen</span><span class="sxs-lookup"><span data-stu-id="ffded-122">Learn how to build applications that render digital content on holographic and VR display devices</span></span> |

### <a name="2-core-building-blocks"></a><span data-ttu-id="ffded-123">2. Grundbausteine</span><span class="sxs-lookup"><span data-stu-id="ffded-123">2. Core building blocks</span></span>

<span data-ttu-id="ffded-124">Nachdem Sie ein neues immersives Projekt begonnen haben, benötigen Sie einige Grundbausteine zum Entwickeln immersiver Apps.</span><span class="sxs-lookup"><span data-stu-id="ffded-124">After starting a new immersive project, you'll need some basic building blocks to develop immersive apps.</span></span> <span data-ttu-id="ffded-125">Alle Hauptbausteine für Mixed Reality-Anwendungen werden in einer Weise verfügbar gemacht, die mit anderen Unity-APIs konsistent ist.</span><span class="sxs-lookup"><span data-stu-id="ffded-125">All of the core building blocks for mixed reality applications are exposed in a manner consistent with other Unity APIs.</span></span> <span data-ttu-id="ffded-126">Sie benötigen sie möglicherweise nicht alle auf einmal, aber wir empfehlen Ihnen, sich frühzeitig mit ihnen vertraut zu machen.</span><span class="sxs-lookup"><span data-stu-id="ffded-126">You might not need all of them at once, but we recommend exploring early on.</span></span> <span data-ttu-id="ffded-127">Nachdem Sie sich mit den unten aufgeführten Grundbausteinen beschäftigt haben, verfügen Sie über eine mit Funktionen angefüllte Toolbox, die Sie in ein VR-Projekt integrieren können.</span><span class="sxs-lookup"><span data-stu-id="ffded-127">After diving into the core building blocks listed below, you'll have a toolbox full of features you can integrate into a VR project.</span></span>

[!INCLUDE[](../includes/unity-building-blocks-wmr.md)]

### <a name="3-platform-capabilities-and-apis"></a><span data-ttu-id="ffded-128">3. Plattformfunktionen und APIs</span><span class="sxs-lookup"><span data-stu-id="ffded-128">3. Platform capabilities and APIs</span></span>

<span data-ttu-id="ffded-129">Andere wichtige Features, die in immersiven Anwendungen eine Rolle spielen, sind über Unity-APIs ohne Zusatzpakete oder Setup verfügbar.</span><span class="sxs-lookup"><span data-stu-id="ffded-129">Other key features that play a role in immersive applications are available through Unity APIs without any extra packages or setup.</span></span> <span data-ttu-id="ffded-130">Nachdem Sie sich mit den erweiterten Funktionen beschäftigt haben, die Unity bietet, werden Sie imstande sein, tiefere, komplexe VR-Apps zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="ffded-130">After diving into the more advanced capabilities that Unity offers, you'll be able to build deeper, complex VR apps.</span></span>

|  <span data-ttu-id="ffded-131">Funktion</span><span class="sxs-lookup"><span data-stu-id="ffded-131">Feature</span></span>  |  <span data-ttu-id="ffded-132">Funktionen</span><span class="sxs-lookup"><span data-stu-id="ffded-132">Capabilities</span></span>  |
| --- | --- |
| [<span data-ttu-id="ffded-133">Verlust der Nachverfolgung</span><span class="sxs-lookup"><span data-stu-id="ffded-133">Tracking loss</span></span>](tracking-loss-in-unity.md) | <span data-ttu-id="ffded-134">Behandeln Sie Szenarien, in denen Ihr Gerät sich im Weltbereich der Anwendung nicht finden kann</span><span class="sxs-lookup"><span data-stu-id="ffded-134">Handle scenarios where your device can't locate itself in the applications world space</span></span> |
| [<span data-ttu-id="ffded-135">Tastatureingabe</span><span class="sxs-lookup"><span data-stu-id="ffded-135">Keyboard input</span></span>](keyboard-input-in-unity.md) | <span data-ttu-id="ffded-136">Rufen Sie Eingaben von realen und Mixed Reality-Tastaturen in Ihren Apps ab</span><span class="sxs-lookup"><span data-stu-id="ffded-136">Get input from real-world and Mixed Reality keyboards in your apps</span></span> |

### <a name="4-deploying-to-a-device-or-emulator"></a><span data-ttu-id="ffded-137">4. Bereitstellen auf einem Gerät oder in einem Emulator</span><span class="sxs-lookup"><span data-stu-id="ffded-137">4. Deploying to a device or emulator</span></span>

<span data-ttu-id="ffded-138">Sobald Sie Ihr Unity-Holografieprojekt bis zur Testreife gebracht haben, besteht der nächste Schritt im Exportieren und Erstellen einer Unity Visual Studio-Projektmappe.</span><span class="sxs-lookup"><span data-stu-id="ffded-138">Once you've got your holographic Unity project ready for testing, your next step is to export and build a Unity Visual Studio solution.</span></span> <span data-ttu-id="ffded-139">Mithilfe dieser VS-Projektmappe können Sie Ihre Anwendung auf realen oder simulierten Geräten ausführen.</span><span class="sxs-lookup"><span data-stu-id="ffded-139">With that VS solution in hand, you can run your application on real or simulated devices.</span></span> <span data-ttu-id="ffded-140">Am Ende dieses Abschnitts können Sie die Anwendung auf einem Gerät oder Emulator bereitstellen, das bzw. der Ihren Entwicklungsanforderungen entspricht.</span><span class="sxs-lookup"><span data-stu-id="ffded-140">By the end of this section, you'll be able to deploy your application on a device or emulator that fits your development needs.</span></span>

* [<span data-ttu-id="ffded-141">Immersives Headset für Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="ffded-141">Windows Mixed Reality immersive headset</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)
* [<span data-ttu-id="ffded-142">Simulator für immersives Headset für Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="ffded-142">Windows Mixed Reality immersive headset simulator</span></span>](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

## <a name="whats-next"></a><span data-ttu-id="ffded-143">Wie geht es weiter?</span><span class="sxs-lookup"><span data-stu-id="ffded-143">What's next?</span></span>

<span data-ttu-id="ffded-144">Die Arbeit eines Entwicklers ist nie getan, insbesondere beim Lernen eines neuen Tools oder SDKs.</span><span class="sxs-lookup"><span data-stu-id="ffded-144">A developers job is never done, especially when learning a new tool or SDK.</span></span> <span data-ttu-id="ffded-145">Die folgenden Abschnitte führen Sie in Gebiete, die jenseits des Materials auf Einstiegsniveau liegen, das Sie bereits durchgearbeitet haben, ergänzt um nützliche Ressourcen, wenn es einmal hakt.</span><span class="sxs-lookup"><span data-stu-id="ffded-145">The following sections can take you into areas beyond the beginner level material you've already completed, along with helpful resources if you get stuck.</span></span> <span data-ttu-id="ffded-146">Beachten Sie, dass diese Themen und Ressourcen keine bestimmte Reihenfolge aufweisen, tauchen Sie also ruhig ein!</span><span class="sxs-lookup"><span data-stu-id="ffded-146">Note that these topics and resources aren't in any sequential order, so feel free to jump around and explore!</span></span>

### <a name="porting"></a><span data-ttu-id="ffded-147">Portieren</span><span class="sxs-lookup"><span data-stu-id="ffded-147">Porting</span></span>

<span data-ttu-id="ffded-148">Wenn Sie über vorhandene Apps verfügen, die Sie portieren möchten, sind die unten aufgeführten Artikel Ihr nächster Anlaufpunkt:</span><span class="sxs-lookup"><span data-stu-id="ffded-148">If you have existing apps that you'd like to port over, the articles listed below are your next stop:</span></span>

* [<span data-ttu-id="ffded-149">Portieren von VR-Apps zu Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="ffded-149">Porting VR apps to Windows Mixed Reality</span></span>](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=project)
* [<span data-ttu-id="ffded-150">Aktualisieren von SteamVR-Apps für Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="ffded-150">Updating SteamVR apps for Windows Mixed Reality</span></span>](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/updating-your-steamvr-application-for-windows-mixed-reality)

### <a name="additional-resources"></a><span data-ttu-id="ffded-151">Zusätzliche Ressourcen</span><span class="sxs-lookup"><span data-stu-id="ffded-151">Additional resources</span></span>

<span data-ttu-id="ffded-152">Bevor Sie sich auf eigene Faust in die Welt der Mixed Reality aufmachen, sollten Sie sich die unten aufgeführte zusätzliche Dokumentation ansehen.</span><span class="sxs-lookup"><span data-stu-id="ffded-152">Before going out into the world of mixed reality on your own, we recommend taking a look at the extra documentation below.</span></span> 

* [<span data-ttu-id="ffded-153">VR-Handbuch für Enthusiasten</span><span class="sxs-lookup"><span data-stu-id="ffded-153">VR enthusiast guide</span></span>](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/vr-journey)
* [<span data-ttu-id="ffded-154">Unity Asset Store</span><span class="sxs-lookup"><span data-stu-id="ffded-154">Unity Asset Store</span></span>](https://www.assetstore.unity3d.com)

## <a name="see-also"></a><span data-ttu-id="ffded-155">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="ffded-155">See also</span></span> 

* [<span data-ttu-id="ffded-156">Empfohlene Einstellungen für Unity</span><span class="sxs-lookup"><span data-stu-id="ffded-156">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="ffded-157">Leistungsempfehlungen für Unity</span><span class="sxs-lookup"><span data-stu-id="ffded-157">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="ffded-158">Exportieren und Erstellen einer Unity-Projektmappe für Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ffded-158">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="ffded-159">Bewährte Methoden für das Arbeiten mit Unity und Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ffded-159">Best practices for working with Unity and Visual Studio</span></span>](best-practices-for-working-with-unity-and-visual-studio.md)
