---
title: Unity-Bereitstellung für VR
description: Beginnen Sie mit dem Entwickeln von Mixed Reality-Apps in Unity für immersive Headsets für VR und Windows Mixed Reality.
author: hferrone
ms.author: kurtie
ms.date: 12/11/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unity, Mixed Reality, Entwicklung, Erste Schritte, neues Projekt, Portieren, Funktion, Kamera, Simulation, Emulation, Dokumentation, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, was ist Virtual Reality, was ist Augmented Reality, MRTK, Mixed Reality Toolkit, Spracheingabe, ausrichtbare Kamera, Emulator, Azure, Tutorials
ms.openlocfilehash: e80c5411c7d180e0d78e031599455235dabaceb7
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2021
ms.locfileid: "102237141"
---
# <a name="unity-development-for-vr-and-windows-mixed-reality"></a><span data-ttu-id="8ab49-104">Unity-Entwicklung für VR und Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="8ab49-104">Unity development for VR and Windows Mixed Reality</span></span>

![Unity-Bannerlogo](../images/unity_logo_banner.png)

<span data-ttu-id="8ab49-106">Wenn Sie mit Unity noch nicht vertraut sind, empfehlen wir Ihnen, sich mit den [Tutorials](https://unity3d.com/learn/tutorials) für Einsteiger auf der Unity-Lernplattform zu befassen, bevor Sie fortfahren.</span><span class="sxs-lookup"><span data-stu-id="8ab49-106">If you're brand new to Unity, we recommend that you explore the beginner level [tutorials](https://unity3d.com/learn/tutorials) on the Unity Learn platform before continuing.</span></span> <span data-ttu-id="8ab49-107">Außerdem ist es eine gute Idee, die [Unity Mixed Reality-Foren](https://forum.unity3d.com/forums/hololens.102/) aufzusuchen, um sich in der Onlinecommunity zu engagieren, die Mixed Reality-Apps erstellt.</span><span class="sxs-lookup"><span data-stu-id="8ab49-107">It's also a good idea to visit the [Unity Mixed Reality forums](https://forum.unity3d.com/forums/hololens.102/) to engage with the online community building mixed reality apps.</span></span> <span data-ttu-id="8ab49-108">Sie können schlicht nicht wissen, welche tollen Medienobjekte oder Lösungen Sie abseits ausgetretener Pfade finden.</span><span class="sxs-lookup"><span data-stu-id="8ab49-108">You never know what cool assets or solutions you might find out in the wild.</span></span> <span data-ttu-id="8ab49-109">Wenn Sie bereit sind, mit dem MRTK loszulegen, gehen Sie zu den Prüfpunkten für die Entwicklung unten!</span><span class="sxs-lookup"><span data-stu-id="8ab49-109">When you're ready to get started with MRTK head to the development checkpoints below!</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8ab49-110">Sehen Sie sich unsere **[Portierungsleitfäden](../porting-apps/porting-overview.md)** an, wenn Sie ein vorhandenes Unity-Projekt auf ein immersives Windows Mixed Reality-Headset portieren möchten.</span><span class="sxs-lookup"><span data-stu-id="8ab49-110">Take a look at our **[porting guides](../porting-apps/porting-overview.md)** if you have an existing Unity project that you want to bring over to a Windows Mixed Reality immersive headset.</span></span> 

## <a name="development-checkpoints"></a><span data-ttu-id="8ab49-111">Prüfpunkte für die Entwicklung</span><span class="sxs-lookup"><span data-stu-id="8ab49-111">Development checkpoints</span></span>

<span data-ttu-id="8ab49-112">Nutzen Sie die folgenden Prüfpunkte, um Ihre Unity-Spiele und Anwendungen in eine Mixed Reality-Welt einzubringen.</span><span class="sxs-lookup"><span data-stu-id="8ab49-112">Use the following checkpoints to bring your Unity games and applications into the world of mixed reality.</span></span> 

### <a name="1-getting-started"></a><span data-ttu-id="8ab49-113">1. Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="8ab49-113">1. Getting started</span></span>

<span data-ttu-id="8ab49-114">Es gibt eine kleine Gruppe von Unity-Einstellungen, die Sie für die Entwicklung für Windows Mixed Reality und VR manuell ändern müssen.</span><span class="sxs-lookup"><span data-stu-id="8ab49-114">There are a small set of Unity settings you'll need to manually change for Windows Mixed Reality and VR development.</span></span> <span data-ttu-id="8ab49-115">Diese gliedern sich in zwei Kategorien: projektbezogene und szenenbezogene.</span><span class="sxs-lookup"><span data-stu-id="8ab49-115">These are broken down into two categories: per-project and per-scene.</span></span> <span data-ttu-id="8ab49-116">Am Ende dieses Abschnitts verfügen Sie über die Tools und Projekteinstellungen, um mit dem Erstellen Ihrer eigenen Apps zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="8ab49-116">By the end of this section, you'll have the tools and project settings to start creating your own apps!</span></span>

|  <span data-ttu-id="8ab49-117">Prüfpunkt</span><span class="sxs-lookup"><span data-stu-id="8ab49-117">Checkpoint</span></span>  |  <span data-ttu-id="8ab49-118">Ergebnis</span><span class="sxs-lookup"><span data-stu-id="8ab49-118">Outcome</span></span>  |
| --- | --- |
| [<span data-ttu-id="8ab49-119">Installieren der neuesten Tools</span><span class="sxs-lookup"><span data-stu-id="8ab49-119">Install the latest tools</span></span>](../install-the-tools.md) | <span data-ttu-id="8ab49-120">Laden Sie das aktuellste Unreal-Paket herunter, installieren Sie es, und richten Sie Ihr Projekt für Mixed Reality ein</span><span class="sxs-lookup"><span data-stu-id="8ab49-120">Download and install the latest Unity package and setup your project for mixed reality</span></span> |
| [<span data-ttu-id="8ab49-121">Konfigurieren Ihres Projekts für WMR</span><span class="sxs-lookup"><span data-stu-id="8ab49-121">Configuring your project for WMR</span></span>](configure-unity-project.md) | <span data-ttu-id="8ab49-122">Erfahren Sie, wie Sie Anwendungen erstellen, die digitale Inhalte auf holografischen und VR-Anzeigegeräten darstellen</span><span class="sxs-lookup"><span data-stu-id="8ab49-122">Learn how to build applications that render digital content on holographic and VR display devices</span></span> |

### <a name="2-core-building-blocks"></a><span data-ttu-id="8ab49-123">2. Grundbausteine</span><span class="sxs-lookup"><span data-stu-id="8ab49-123">2. Core building blocks</span></span>

<span data-ttu-id="8ab49-124">Nachdem Sie ein neues immersives Projekt begonnen haben, benötigen Sie einige Grundbausteine zum Entwickeln immersiver Apps.</span><span class="sxs-lookup"><span data-stu-id="8ab49-124">After starting a new immersive project, you'll need some basic building blocks to develop immersive apps.</span></span> <span data-ttu-id="8ab49-125">Alle Hauptbausteine für Mixed Reality-Anwendungen werden in einer Weise verfügbar gemacht, die mit anderen Unity-APIs konsistent ist.</span><span class="sxs-lookup"><span data-stu-id="8ab49-125">All of the core building blocks for mixed reality applications are exposed in a manner consistent with other Unity APIs.</span></span> <span data-ttu-id="8ab49-126">Sie benötigen sie möglicherweise nicht alle auf einmal, aber wir empfehlen Ihnen, sich frühzeitig mit ihnen vertraut zu machen.</span><span class="sxs-lookup"><span data-stu-id="8ab49-126">You might not need all of them at once, but we recommend exploring early on.</span></span> <span data-ttu-id="8ab49-127">Nachdem Sie sich mit den unten aufgeführten Grundbausteinen beschäftigt haben, verfügen Sie über eine mit Funktionen angefüllte Toolbox, die Sie in ein VR-Projekt integrieren können.</span><span class="sxs-lookup"><span data-stu-id="8ab49-127">After diving into the core building blocks listed below, you'll have a toolbox full of features you can integrate into a VR project.</span></span>

[!INCLUDE[](../includes/unity-building-blocks-wmr.md)]

### <a name="3-advanced-features"></a><span data-ttu-id="8ab49-128">3. Erweiterte Features</span><span class="sxs-lookup"><span data-stu-id="8ab49-128">3. Advanced features</span></span>

<span data-ttu-id="8ab49-129">Andere wichtige Features, die in immersiven Anwendungen eine Rolle spielen, sind über Unity-APIs ohne Zusatzpakete oder Setup verfügbar.</span><span class="sxs-lookup"><span data-stu-id="8ab49-129">Other key features that play a role in immersive applications are available through Unity APIs without any extra packages or setup.</span></span> <span data-ttu-id="8ab49-130">Nachdem Sie sich mit den erweiterten Funktionen beschäftigt haben, die Unity bietet, werden Sie imstande sein, tiefere, komplexe VR-Apps zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="8ab49-130">After diving into the more advanced capabilities that Unity offers, you'll be able to build deeper, complex VR apps.</span></span>

|  <span data-ttu-id="8ab49-131">Funktion</span><span class="sxs-lookup"><span data-stu-id="8ab49-131">Feature</span></span>  |  <span data-ttu-id="8ab49-132">Funktionen</span><span class="sxs-lookup"><span data-stu-id="8ab49-132">Capabilities</span></span>  |
| --- | --- |
| [<span data-ttu-id="8ab49-133">Verlust der Nachverfolgung</span><span class="sxs-lookup"><span data-stu-id="8ab49-133">Tracking loss</span></span>](tracking-loss-in-unity.md) | <span data-ttu-id="8ab49-134">Behandeln Sie Szenarien, in denen Ihr Gerät sich im Weltbereich der Anwendung nicht finden kann</span><span class="sxs-lookup"><span data-stu-id="8ab49-134">Handle scenarios where your device can't locate itself in the applications world space</span></span> |
| [<span data-ttu-id="8ab49-135">Tastatureingabe</span><span class="sxs-lookup"><span data-stu-id="8ab49-135">Keyboard input</span></span>](keyboard-input-in-unity.md) | <span data-ttu-id="8ab49-136">Rufen Sie Eingaben von realen und Mixed Reality-Tastaturen in Ihren Apps ab</span><span class="sxs-lookup"><span data-stu-id="8ab49-136">Get input from real-world and Mixed Reality keyboards in your apps</span></span> |

### <a name="4-deploying-to-a-device-or-emulator"></a><span data-ttu-id="8ab49-137">4. Bereitstellen auf einem Gerät oder in einem Emulator</span><span class="sxs-lookup"><span data-stu-id="8ab49-137">4. Deploying to a device or emulator</span></span>

<span data-ttu-id="8ab49-138">Sobald Sie Ihr Unity-Holografieprojekt bis zur Testreife gebracht haben, besteht der nächste Schritt im Exportieren und Erstellen einer Unity Visual Studio-Projektmappe.</span><span class="sxs-lookup"><span data-stu-id="8ab49-138">Once you've got your holographic Unity project ready for testing, your next step is to export and build a Unity Visual Studio solution.</span></span> <span data-ttu-id="8ab49-139">Mithilfe dieser VS-Projektmappe können Sie Ihre Anwendung auf realen oder simulierten Geräten ausführen.</span><span class="sxs-lookup"><span data-stu-id="8ab49-139">With that VS solution in hand, you can run your application on real or simulated devices.</span></span> <span data-ttu-id="8ab49-140">Am Ende dieses Abschnitts können Sie die Anwendung auf einem Gerät oder Emulator bereitstellen, das bzw. der Ihren Entwicklungsanforderungen entspricht.</span><span class="sxs-lookup"><span data-stu-id="8ab49-140">By the end of this section, you'll be able to deploy your application on a device or emulator that fits your development needs.</span></span>

* [<span data-ttu-id="8ab49-141">Immersives Headset für Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="8ab49-141">Windows Mixed Reality immersive headset</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)
* [<span data-ttu-id="8ab49-142">Simulator für immersives Headset für Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="8ab49-142">Windows Mixed Reality immersive headset simulator</span></span>](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

## <a name="whats-next"></a><span data-ttu-id="8ab49-143">Wie geht es weiter?</span><span class="sxs-lookup"><span data-stu-id="8ab49-143">What's next?</span></span>

<span data-ttu-id="8ab49-144">Die Arbeit eines Entwicklers ist nie getan, insbesondere beim Lernen eines neuen Tools oder SDKs.</span><span class="sxs-lookup"><span data-stu-id="8ab49-144">A developers job is never done, especially when learning a new tool or SDK.</span></span> <span data-ttu-id="8ab49-145">Die folgenden Abschnitte führen Sie in Gebiete, die jenseits des Materials auf Einstiegsniveau liegen, das Sie bereits durchgearbeitet haben, ergänzt um nützliche Ressourcen, wenn es einmal hakt.</span><span class="sxs-lookup"><span data-stu-id="8ab49-145">The following sections can take you into areas beyond the beginner level material you've already completed, along with helpful resources if you get stuck.</span></span> <span data-ttu-id="8ab49-146">Beachten Sie, dass diese Themen und Ressourcen keine bestimmte Reihenfolge aufweisen, tauchen Sie also ruhig ein!</span><span class="sxs-lookup"><span data-stu-id="8ab49-146">Note that these topics and resources aren't in any sequential order, so feel free to jump around and explore!</span></span>

### <a name="porting"></a><span data-ttu-id="8ab49-147">Portieren</span><span class="sxs-lookup"><span data-stu-id="8ab49-147">Porting</span></span>

<span data-ttu-id="8ab49-148">Wenn Sie über vorhandene Apps verfügen, die Sie portieren möchten, sind die unten aufgeführten Artikel Ihr nächster Anlaufpunkt:</span><span class="sxs-lookup"><span data-stu-id="8ab49-148">If you have existing apps that you'd like to port over, the articles listed below are your next stop:</span></span>

* [<span data-ttu-id="8ab49-149">Portieren von VR-Apps zu Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="8ab49-149">Porting VR apps to Windows Mixed Reality</span></span>](../porting-apps/porting-guides.md?tabs=project)
* [<span data-ttu-id="8ab49-150">Aktualisieren von SteamVR-Apps für Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="8ab49-150">Updating SteamVR apps for Windows Mixed Reality</span></span>](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md)

### <a name="additional-resources"></a><span data-ttu-id="8ab49-151">Zusätzliche Ressourcen</span><span class="sxs-lookup"><span data-stu-id="8ab49-151">Additional resources</span></span>

<span data-ttu-id="8ab49-152">Bevor Sie sich auf eigene Faust in die Welt der Mixed Reality aufmachen, sollten Sie sich die unten aufgeführte zusätzliche Dokumentation ansehen.</span><span class="sxs-lookup"><span data-stu-id="8ab49-152">Before going out into the world of mixed reality on your own, we recommend taking a look at the extra documentation below.</span></span> 

* [<span data-ttu-id="8ab49-153">VR-Handbuch für Enthusiasten</span><span class="sxs-lookup"><span data-stu-id="8ab49-153">VR enthusiast guide</span></span>](/windows/mixed-reality/enthusiast-guide/vr-journey)
* [<span data-ttu-id="8ab49-154">Unity Asset Store</span><span class="sxs-lookup"><span data-stu-id="8ab49-154">Unity Asset Store</span></span>](https://assetstore.unity.com)

## <a name="see-also"></a><span data-ttu-id="8ab49-155">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="8ab49-155">See also</span></span> 

* [<span data-ttu-id="8ab49-156">Empfohlene Einstellungen für Unity</span><span class="sxs-lookup"><span data-stu-id="8ab49-156">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="8ab49-157">Leistungsempfehlungen für Unity</span><span class="sxs-lookup"><span data-stu-id="8ab49-157">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="8ab49-158">Exportieren und Erstellen einer Unity-Projektmappe für Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8ab49-158">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="8ab49-159">Bewährte Methoden für das Arbeiten mit Unity und Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8ab49-159">Best practices for working with Unity and Visual Studio</span></span>](best-practices-for-working-with-unity-and-visual-studio.md)