---
title: Erstellen einer PC-Anwendung für Holographic Remoting
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie eine Anwendung erstellen, die Mixed Reality-Remoting von Ihrem PC zu HoloLens 2 ausführt.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, Holographic Remoting am PC, Visual Studio
ms.localizationpriority: high
ms.openlocfilehash: ca0efe13acac4408a05ab89eb98b508e9993c5a4
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392539"
---
# <a name="2-creating-a-holographic-remoting-pc-application"></a><span data-ttu-id="728de-104">2. Erstellen einer PC-Anwendung für Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="728de-104">2. Creating a Holographic Remoting PC application</span></span>

<span data-ttu-id="728de-105">In diesem Tutorial erfahren Sie, wie Sie eine PC-App für Holographic Remoting erstellen und zu einem beliebigen Zeitpunkt eine Verbindung mit HoloLens 2 herstellen. Auf diese Weise können Sie 3D-Inhalte in Mixed Reality visualisieren.</span><span class="sxs-lookup"><span data-stu-id="728de-105">In this tutorial, you will learn how to create a PC app for Holographic Remoting and connect to HoloLens 2 at any point, providing a way to visualize 3D content in mixed reality.</span></span>

## <a name="objectives"></a><span data-ttu-id="728de-106">Ziele</span><span class="sxs-lookup"><span data-stu-id="728de-106">Objectives</span></span>

* <span data-ttu-id="728de-107">Konfigurieren von Unity für Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="728de-107">Configure Unity for Holographic Remoting</span></span>
* <span data-ttu-id="728de-108">Erfahren Sie, wie Sie die Anwendung mit Visual Studio erstellen und bereitstellen</span><span class="sxs-lookup"><span data-stu-id="728de-108">Learn how to build and deploy the application with Visual Studio</span></span>
* <span data-ttu-id="728de-109">Entwickeln von Holographic Remoting-Anwendungen und Herstellen einer Verbindung mit HoloLens</span><span class="sxs-lookup"><span data-stu-id="728de-109">Developing Holographic Remoting application and connecting to HoloLens</span></span>

## <a name="configuring-the-capabilities"></a><span data-ttu-id="728de-110">Konfigurieren der Funktionen</span><span class="sxs-lookup"><span data-stu-id="728de-110">Configuring the capabilities</span></span>

<span data-ttu-id="728de-111">Erweitern Sie im Fenster **Projekteinstellungen** die **Veröffentlichungseinstellungen**, scrollen Sie nach unten zum Bereich „Funktionen“, und aktivieren Sie zusätzlich zu den vorhandenen Funktionen das unten angezeigte Funktionskontrollkästchen.</span><span class="sxs-lookup"><span data-stu-id="728de-111">In the **Project Settings** window, expand the **Publishing Settings**, scroll down to the Capabilities section and select the below-shown capability checkbox in addition to the existing capabilities.</span></span>

* <span data-ttu-id="728de-112">Internet Client Server</span><span class="sxs-lookup"><span data-stu-id="728de-112">Internet Clint server</span></span>
* <span data-ttu-id="728de-113">Privates Netzwerk Client Server</span><span class="sxs-lookup"><span data-stu-id="728de-113">Private Network Client Server</span></span>

![Aktivieren von Funktionen](images/mrlearning-pc-holographic-remoting/tutorial2-section0-step1-1.png)

[!INCLUDE[](includes/configuring-scene-for-holographic-remoting.md)]

## <a name="build-your-application-to-pc"></a><span data-ttu-id="728de-115">Erstellen Ihrer Anwendung auf dem PC</span><span class="sxs-lookup"><span data-stu-id="728de-115">Build your application to PC</span></span>

<span data-ttu-id="728de-116">Ihre Holographic Remoting-App kann jetzt auf Ihrem PC erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="728de-116">Your Holographic Remoting app is now ready to build on your PC.</span></span> <span data-ttu-id="728de-117">Führen Sie die folgenden Schritte aus, und nehmen Sie diese Änderungen vor, um die Anwendung auf Ihrem PC zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="728de-117">Follow the below steps and make these changes to build this application on to your PC.</span></span>

[!INCLUDE[](includes/build-your-application-to-pc.md)]

## <a name="testing-holographic-remoting-remote-application"></a><span data-ttu-id="728de-118">Testen einer Holographic Remoting-Remoteanwendung</span><span class="sxs-lookup"><span data-stu-id="728de-118">Testing Holographic Remoting remote application</span></span>

<span data-ttu-id="728de-119">Zum Herstellen einer Verbindung Ihrer PC-Anwendung mit HoloLens 2 führen Sie den folgenden Prozess aus:</span><span class="sxs-lookup"><span data-stu-id="728de-119">To connect your PC application to your HoloLens 2, follow the below process:</span></span>

### <a name="1-install-the-remoting-player-application-on-hololens-2-device"></a><span data-ttu-id="728de-120">1. Installieren der Remoting Player-Anwendung auf HoloLens 2-Geräten</span><span class="sxs-lookup"><span data-stu-id="728de-120">1. Install the Remoting Player application on HoloLens 2 device</span></span>

* <span data-ttu-id="728de-121">Besuchen Sie auf dem HoloLens 2-Gerät die Store-App, und suchen Sie nach „**Remoting Player**“.</span><span class="sxs-lookup"><span data-stu-id="728de-121">On your HoloLens 2, visit the Store app and search for "**Remoting Player**."</span></span>
* <span data-ttu-id="728de-122">Wählen Sie die **Remoting Player**-App aus.</span><span class="sxs-lookup"><span data-stu-id="728de-122">Select the **Remoting Player** app.</span></span>
* <span data-ttu-id="728de-123">Tippen Sie auf **Installieren**, um die App herunterzuladen und zu installieren.</span><span class="sxs-lookup"><span data-stu-id="728de-123">Tap **Install** to download and install the app.</span></span>

### <a name="2-connect-the-holographic-remoting-pc-app-to-the-remoting-player"></a><span data-ttu-id="728de-124">2. Verbinden der PC-App für Holographic Remoting mit dem Remoting Player</span><span class="sxs-lookup"><span data-stu-id="728de-124">2. Connect the Holographic remoting PC app to the Remoting Player</span></span>

* <span data-ttu-id="728de-125">Starten Sie den **Remoting Player** auf Ihrem HoloLens-Gerät.</span><span class="sxs-lookup"><span data-stu-id="728de-125">Start the **Remoting Player** on your HoloLens.</span></span>
* <span data-ttu-id="728de-126">Notieren Sie sich die HoloLens-**IP-Adresse**.</span><span class="sxs-lookup"><span data-stu-id="728de-126">Take note of the HoloLens **IP address**.</span></span> <span data-ttu-id="728de-127">Sie wird vom **Remoting Player** als Hologramm angezeigt, sobald er gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="728de-127">It will be displayed as a hologram by the **Remoting Player** as soon as it launches.</span></span>
* <span data-ttu-id="728de-128">Öffnen Sie die PC-Anwendung für Holographic Remoting auf Ihrem PC.</span><span class="sxs-lookup"><span data-stu-id="728de-128">Open the Holographic Remoting PC application on your PC.</span></span>
* <span data-ttu-id="728de-129">Nachdem die Anwendung gestartet wurde, geben Sie die **IP-Adresse** ein, und klicken Sie auf die Schaltfläche **Connect** (Verbinden), um eine Verbindung herzustellen.</span><span class="sxs-lookup"><span data-stu-id="728de-129">Once the application is launched, enter the **IP address** and click on the **Connect**  button to connect.</span></span>

## <a name="congratulations"></a><span data-ttu-id="728de-130">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="728de-130">Congratulations</span></span>

<span data-ttu-id="728de-131">In diesem Tutorial haben Sie erfahren, wie Sie eine Remote-App für Holographic Remoting erstellen und zu einem beliebigen Zeitpunkt eine Verbindung mit HoloLens 2 herstellen. Auf diese Weise können Sie 3D-Inhalte in Mixed Reality visualisieren.</span><span class="sxs-lookup"><span data-stu-id="728de-131">In this tutorial, you learned how to create a Holographic Remoting remote app and connect to HoloLens 2 at any point, providing a way to visualize 3D content in mixed reality.</span></span> <span data-ttu-id="728de-132">Sobald das HoloLens-Gerät eine Verbindung mit der PC-Anwendung für Holographic Remoting hergestellt hat, sollte die Mixed Reality-Lösung auf das HoloLens 2-Gerät gestreamt werden.</span><span class="sxs-lookup"><span data-stu-id="728de-132">Once the HoloLens connected to the Holographic Remoting PC application, you should see the mixed reality experience streaming into your HoloLens 2 device.</span></span>
