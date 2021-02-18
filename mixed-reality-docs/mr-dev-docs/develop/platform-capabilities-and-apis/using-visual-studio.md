---
title: Verwenden von Visual Studio zum Bereitstellen und Debuggen
description: Erfahren Sie, wie Sie Apps für HoloLens und Windows Mixed Reality mithilfe von Visual Studio erstellen, debuggen und bereitstellen.
author: pbarnettms
ms.author: pbarnett
ms.date: 04/13/2020
ms.topic: article
ms.localizationpriority: high
keywords: Visual Studio, HoloLens, Mixed Reality, debuggen, bereitstellen
ms.openlocfilehash: 2ab89311163a48ee3c14511446a1498ce883a232
ms.sourcegitcommit: 029f247a6c33068360d3a06f2a473a12586017e1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100496092"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a><span data-ttu-id="3cba3-104">Verwenden von Visual Studio zum Bereitstellen und Debuggen</span><span class="sxs-lookup"><span data-stu-id="3cba3-104">Using Visual Studio to deploy and debug</span></span>

<span data-ttu-id="3cba3-105">Unabhängig davon, ob Sie DirectX oder Unity zur Entwicklung ihrer Mixed Reality-App verwenden, Visual Studio ist Ihr Tool der Wahl zum Debuggen und Bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="3cba3-105">Whether you're using DirectX or Unity to develop your mixed reality app, Visual Studio is your go-to tool for debugging and deployment.</span></span> <span data-ttu-id="3cba3-106">In diesem Abschnitt wird Folgendes erläutert:</span><span class="sxs-lookup"><span data-stu-id="3cba3-106">In this section, you will learn how to:</span></span>
* <span data-ttu-id="3cba3-107">Bereitstellen von Anwendungen auf Ihrer HoloLens oder Ihrem immersiven Windows Mixed Reality-Headset mithilfe von Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3cba3-107">Deploy applications to your HoloLens or Windows Mixed Reality immersive headset through Visual Studio.</span></span>
* <span data-ttu-id="3cba3-108">Verwenden des in Visual Studio integrierten HoloLens-Emulators.</span><span class="sxs-lookup"><span data-stu-id="3cba3-108">Use the HoloLens emulator built in to Visual Studio.</span></span>
* <span data-ttu-id="3cba3-109">Debuggen von Mixed Reality-Apps.</span><span class="sxs-lookup"><span data-stu-id="3cba3-109">Debug mixed reality apps.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3cba3-110">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="3cba3-110">Prerequisites</span></span>

1. <span data-ttu-id="3cba3-111">Installationsanweisungen finden Sie unter [Installieren der Tools](../../develop/install-the-tools.md#installation-checklist).</span><span class="sxs-lookup"><span data-stu-id="3cba3-111">See [Install the Tools](../../develop/install-the-tools.md#installation-checklist) for installation instructions.</span></span>
2. <span data-ttu-id="3cba3-112">Erstellen Sie ein neues Projekt für Universelle Windows-Apps in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3cba3-112">Create a new Universal Windows app project in Visual Studio.</span></span>  <span data-ttu-id="3cba3-113">Verwenden Sie für HoloLens (1. Gen.) Visual Studio 2017 oder höher.</span><span class="sxs-lookup"><span data-stu-id="3cba3-113">For HoloLens (1st gen), use Visual Studio 2017 or newer.</span></span>  <span data-ttu-id="3cba3-114">Verwenden Sie für HoloLens 2 Visual Studio 2019 16.2 oder höher.</span><span class="sxs-lookup"><span data-stu-id="3cba3-114">For HoloLens 2, use Visual Studio 2019 16.2 or newer.</span></span> <span data-ttu-id="3cba3-115">C# und C++ werden unterstützt.</span><span class="sxs-lookup"><span data-stu-id="3cba3-115">C# and C++ are supported.</span></span> <span data-ttu-id="3cba3-116">(Oder befolgen Sie die Anweisungen zum [Erstellen einer App in Unity](../../develop/unity/tutorials/holograms-100.md).)</span><span class="sxs-lookup"><span data-stu-id="3cba3-116">(Or follow the instructions to [create an app in Unity](../../develop/unity/tutorials/holograms-100.md).)</span></span>

## <a name="enabling-developer-mode"></a><span data-ttu-id="3cba3-117">Aktivieren des Entwicklermodus</span><span class="sxs-lookup"><span data-stu-id="3cba3-117">Enabling Developer Mode</span></span>

<span data-ttu-id="3cba3-118">Aktivieren Sie zunächst den **Entwicklermodus** auf Ihrem Gerät, damit Visual Studio eine Verbindung damit herstellen kann.</span><span class="sxs-lookup"><span data-stu-id="3cba3-118">Start by enabling **Developer Mode** on your device, so Visual Studio can connect to it.</span></span>

### <a name="hololens"></a><span data-ttu-id="3cba3-119">HoloLens</span><span class="sxs-lookup"><span data-stu-id="3cba3-119">HoloLens</span></span>

1. <span data-ttu-id="3cba3-120">Schalten Sie die HoloLens ein, und setzen Sie sie auf.</span><span class="sxs-lookup"><span data-stu-id="3cba3-120">Turn on your HoloLens and put on the device.</span></span>
2. <span data-ttu-id="3cba3-121">Verwenden Sie die [Startgeste](../../design/system-gesture.md), um das Hauptmenü zu starten.</span><span class="sxs-lookup"><span data-stu-id="3cba3-121">Use the [start gesture](../../design/system-gesture.md) to launch the main menu.</span></span>
3. <span data-ttu-id="3cba3-122">Wählen Sie die Kachel **Einstellungen** aus, um die App in Ihrer Umgebung zu starten.</span><span class="sxs-lookup"><span data-stu-id="3cba3-122">Select the **Settings** tile to launch the app in your environment.</span></span>
4. <span data-ttu-id="3cba3-123">Wählen Sie das Menüelement **Aktualisieren** aus.</span><span class="sxs-lookup"><span data-stu-id="3cba3-123">Select the **Update** menu item.</span></span>
5. <span data-ttu-id="3cba3-124">Wählen Sie das Menüelement **Für Entwickler** aus.</span><span class="sxs-lookup"><span data-stu-id="3cba3-124">Select the **For developers** menu item.</span></span>
6. <span data-ttu-id="3cba3-125">Aktivieren Sie den **Entwicklermodus**, um auf Ihrer HoloLens Apps aus Visual Studio bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="3cba3-125">Enable **Developer Mode** to deploy apps from Visual Studio to your HoloLens.</span></span>
7. <span data-ttu-id="3cba3-126">Optional: Scrollen Sie nach unten, und aktivieren Sie auch das **Geräteportal**, mit dem Sie sich über einen Webbrowser mit dem [Windows-Geräteportal](using-the-windows-device-portal.md) auf Ihrer HoloLens verbinden können.</span><span class="sxs-lookup"><span data-stu-id="3cba3-126">Optional: Scroll down and also enable **Device Portal**, which lets you connect to the [Windows Device Portal](using-the-windows-device-portal.md) on your HoloLens from a web browser.</span></span>

### <a name="windows-pc"></a><span data-ttu-id="3cba3-127">Windows PC</span><span class="sxs-lookup"><span data-stu-id="3cba3-127">Windows PC</span></span>

<span data-ttu-id="3cba3-128">Wenn Sie mit einem Windows Mixed Reality-Headset arbeiten, das mit dem PC verbunden ist, müssen Sie den **Entwicklermodus** auf dem PC aktivieren.</span><span class="sxs-lookup"><span data-stu-id="3cba3-128">If you're working with a Windows Mixed Reality headset connected to your PC, you must enable **Developer Mode** on the PC.</span></span>
1. <span data-ttu-id="3cba3-129">Navigieren Sie zu **Einstellungen**</span><span class="sxs-lookup"><span data-stu-id="3cba3-129">Go to **Settings**</span></span>
2. <span data-ttu-id="3cba3-130">Wählen Sie **Update und Sicherheit** aus</span><span class="sxs-lookup"><span data-stu-id="3cba3-130">Select **Update and Security**</span></span>
3. <span data-ttu-id="3cba3-131">Wählen Sie **Für Entwickler** aus</span><span class="sxs-lookup"><span data-stu-id="3cba3-131">Select **For developers**</span></span>
4. <span data-ttu-id="3cba3-132">Aktivieren Sie den **Entwicklermodus**, lesen Sie den Haftungsausschluss für die ausgewählte Einstellung, und wählen Sie dann „Ja“ aus, um die Änderung zu übernehmen.</span><span class="sxs-lookup"><span data-stu-id="3cba3-132">Enable **Developer Mode**, read the disclaimer for the setting you chose, then select Yes to accept the change.</span></span>

## <a name="deploying-a-hololens-app-over-wi-fi"></a><span data-ttu-id="3cba3-133">Bereitstellen einer HoloLens-App über WLAN</span><span class="sxs-lookup"><span data-stu-id="3cba3-133">Deploying a HoloLens app over Wi-Fi</span></span> 

<span data-ttu-id="3cba3-134">Konfigurieren Sie Ihr Visual Studio-Projekt mit den folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="3cba3-134">Configure your Visual Studio project with the following properties:</span></span>

1. <span data-ttu-id="3cba3-135">Wählen Sie die Optionen für die Kompilierung von Apps aus</span><span class="sxs-lookup"><span data-stu-id="3cba3-135">Select your apps compilation options</span></span>
    * <span data-ttu-id="3cba3-136">Wählen Sie für Unity-Projekte entweder **Release** oder **Master** aus</span><span class="sxs-lookup"><span data-stu-id="3cba3-136">For Unity projects, choose either **Release** or **Master**</span></span> 
    * <span data-ttu-id="3cba3-137">Wählen Sie für alle anderen Projekte **Release** aus</span><span class="sxs-lookup"><span data-stu-id="3cba3-137">For all other projects, choose **Release**</span></span>

> [!NOTE]
> <span data-ttu-id="3cba3-138">Umfassende Definitionen für jede der Kompilierungsoptionen finden Sie unter [Exportieren und Entwickeln von Visual Studio-Projektmappen](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).</span><span class="sxs-lookup"><span data-stu-id="3cba3-138">You can find complete definitions for each compilation option in [exporting and building Visual Studio solutions](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).</span></span>

2. <span data-ttu-id="3cba3-139">Wählen Sie Ihre Buildkonfiguration ausgehend von Ihrem Gerät aus.</span><span class="sxs-lookup"><span data-stu-id="3cba3-139">Select your build configuration based on your device</span></span>

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. <span data-ttu-id="3cba3-140">Wählen Sie im Dropdownmenü für das Bereitstellungsziel **Remotecomputer** aus</span><span class="sxs-lookup"><span data-stu-id="3cba3-140">Select **Remote Machine** in the deployment target drop-down menu</span></span>

![Bereitstellungsziel „Remotecomputer“ in Visual Studio](images/remotemachinesetting_arm64.png)

<span data-ttu-id="3cba3-142">Als nächstes müssen Sie die Remoteverbindung festlegen.</span><span class="sxs-lookup"><span data-stu-id="3cba3-142">Next, you need to set your remote connection.</span></span> <span data-ttu-id="3cba3-143">Navigieren Sie für C++- und JavaScript-Projekte zu **Projekt > Eigenschaften > Konfigurationseigenschaften > Debuggen**.</span><span class="sxs-lookup"><span data-stu-id="3cba3-143">For C++ and JavaScript projects, go to **Project > Properties > Configuration Properties > Debugging**.</span></span> <span data-ttu-id="3cba3-144">Wenn Sie in einem C#-Projekt arbeiten, sollte automatisch ein Dialogfeld angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="3cba3-144">If you're working in a C# project, a dialog should automatically appear.</span></span>

> [!NOTE]
> <span data-ttu-id="3cba3-145">Wenn das Dialogfeld für die Remoteverbindung nicht in Ihrem C#-Projekt angezeigt wird, können Sie es manuell über **Eigenschaften > Debuggen** öffnen.</span><span class="sxs-lookup"><span data-stu-id="3cba3-145">If the remote connection dialog doesn't appear in your C# project, you can open it manually from **Properties > Debug**.</span></span>

1. <span data-ttu-id="3cba3-146">Geben Sie die IP-Adresse Ihres Geräts im Feld **Adresse** oder **Computername** ein.</span><span class="sxs-lookup"><span data-stu-id="3cba3-146">Enter the IP address of your device in the **Address** or **Machine Name** field.</span></span> 
    * <span data-ttu-id="3cba3-147">Sie finden die IP-Adresse Ihrer HoloLens unter **Einstellungen > Netzwerk und Internet > Erweiterte Optionen**</span><span class="sxs-lookup"><span data-stu-id="3cba3-147">You can find the IP address on your HoloLens under **Settings > Network & Internet > Advanced Options**</span></span>
    * <span data-ttu-id="3cba3-148">Wir empfehlen, die IP-Adresse immer manuell einzugeben, statt sich auf die Funktion zur automatischen Erkennung zu verlassen.</span><span class="sxs-lookup"><span data-stu-id="3cba3-148">We always recommend manually entering your IP address rather than depending on the Auto Detected feature</span></span>

2. <span data-ttu-id="3cba3-149">Legen Sie den **Authentifizierungsmodus** auf **Universell (Unverschlüsseltes Protokoll)** fest.</span><span class="sxs-lookup"><span data-stu-id="3cba3-149">Set the **Authentication Mode** to **Universal (Unencrypted protocol)**</span></span>

  ![Dialogfeld „Remoteverbindung“ in Visual Studio](images/remotedeploy.png)

3. <span data-ttu-id="3cba3-151">Sie können Ihre App ganz nach Ihren Anforderungen erstellen, bereitstellen und debuggen.</span><span class="sxs-lookup"><span data-stu-id="3cba3-151">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="3cba3-152">Wählen Sie **Debuggen > Debuggen starten** aus, um Ihre App bereitzustellen und den Debugvorgang zu starten.</span><span class="sxs-lookup"><span data-stu-id="3cba3-152">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="3cba3-153">Wählen Sie **Erstellen > Bereitstellen** aus, um eine Erstellung und Bereitstellung ohne Debuggen auszuführen.</span><span class="sxs-lookup"><span data-stu-id="3cba3-153">Select **Build > Deploy** to build and deploy without debugging</span></span>

![Starten ohne Debuggen in Visual Studio](images/deploywithdebugging.png)

4. <span data-ttu-id="3cba3-155">Beim erstmaligen Bereitstellen einer App in Ihrer HoloLens von Ihrem Computer aus werden Sie zur Eingabe einer PIN aufgefordert.</span><span class="sxs-lookup"><span data-stu-id="3cba3-155">The first time you deploy an app to your HoloLens from your PC, you'll be prompted for a PIN.</span></span> <span data-ttu-id="3cba3-156">Befolgen Sie die Anweisungen unten zum **Koppeln Ihres Geräts**.</span><span class="sxs-lookup"><span data-stu-id="3cba3-156">Follow the **Pairing your device** instructions below.</span></span>

## <a name="deploying-a-hololens-app-over-usb"></a><span data-ttu-id="3cba3-157">Bereitstellen einer HoloLens-App über USB</span><span class="sxs-lookup"><span data-stu-id="3cba3-157">Deploying a HoloLens app over USB</span></span> 

<br>

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Deploying-your-HoloLens-2-application/player?format=ny]

1. <span data-ttu-id="3cba3-158">Wählen Sie die Optionen für die Kompilierung von Apps aus</span><span class="sxs-lookup"><span data-stu-id="3cba3-158">Select your apps compilation options</span></span>
    * <span data-ttu-id="3cba3-159">Wählen Sie für Unity-Projekte entweder **Release** oder **Master** aus</span><span class="sxs-lookup"><span data-stu-id="3cba3-159">For Unity projects, choose either **Release** or **Master**</span></span> 
    * <span data-ttu-id="3cba3-160">Wählen Sie für alle anderen Projekte **Release** aus</span><span class="sxs-lookup"><span data-stu-id="3cba3-160">For all other projects, choose **Release**</span></span>

> [!NOTE]
> <span data-ttu-id="3cba3-161">Umfassende Definitionen für jede der Kompilierungsoptionen finden Sie unter [Exportieren und Entwickeln von Visual Studio-Projektmappen](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).</span><span class="sxs-lookup"><span data-stu-id="3cba3-161">You can find complete definitions for each compilation option in [exporting and building Visual Studio solutions](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).</span></span>

2. <span data-ttu-id="3cba3-162">Wählen Sie Ihre Buildkonfiguration ausgehend von Ihrem Gerät aus.</span><span class="sxs-lookup"><span data-stu-id="3cba3-162">Select your build configuration based on your device</span></span>

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. <span data-ttu-id="3cba3-163">Wählen Sie im Dropdownmenü für das Bereitstellungsziel **Gerät** aus</span><span class="sxs-lookup"><span data-stu-id="3cba3-163">Select **Device** in the deployment target drop-down menu</span></span>

![Gerätebereitstellung in Visual Studio](images/buildsettingsusbdeploy_arm64.png)

4. <span data-ttu-id="3cba3-165">Sie können Ihre App ganz nach Ihren Anforderungen erstellen, bereitstellen und debuggen.</span><span class="sxs-lookup"><span data-stu-id="3cba3-165">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="3cba3-166">Wählen Sie **Debuggen > Debuggen starten** aus, um Ihre App bereitzustellen und den Debugvorgang zu starten.</span><span class="sxs-lookup"><span data-stu-id="3cba3-166">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="3cba3-167">Wählen Sie **Erstellen > Bereitstellen** aus, um eine Erstellung und Bereitstellung ohne Debuggen auszuführen.</span><span class="sxs-lookup"><span data-stu-id="3cba3-167">Select **Build > Deploy** to build and deploy without debugging</span></span>

![Starten ohne Debuggen in Visual Studio](images/deploywithdebugging.png)</br>

5. <span data-ttu-id="3cba3-169">Beim erstmaligen Bereitstellen einer App in Ihrer HoloLens von Ihrem Computer aus werden Sie zur Eingabe einer PIN aufgefordert.</span><span class="sxs-lookup"><span data-stu-id="3cba3-169">The first time you deploy an app to your HoloLens from your PC, you'll be prompted for a PIN.</span></span> <span data-ttu-id="3cba3-170">Befolgen Sie die Anweisungen unten zum **Koppeln Ihres Geräts**.</span><span class="sxs-lookup"><span data-stu-id="3cba3-170">Follow the **Pairing your device** instructions below.</span></span>

> [!NOTE]
> <span data-ttu-id="3cba3-171">Wenn Sie bei der Bereitstellung Ihrer Apps über USB eine beträchtliche Verzögerung feststellen, empfehlen wir, die [Anweisungen für Remotecomputer](#deploying-a-hololens-app-over-wi-fi) im vorhergehenden Abschnitt umzusetzen.</span><span class="sxs-lookup"><span data-stu-id="3cba3-171">If you're seeing considerable lag time with your apps deployment over USB, we recommend using the [remote machine instructions](#deploying-a-hololens-app-over-wi-fi) in the previous section.</span></span>

## <a name="deploying-an-app-to-the-hololens-emulator"></a><span data-ttu-id="3cba3-172">Bereitstellen einer App auf dem HoloLens-Emulator</span><span class="sxs-lookup"><span data-stu-id="3cba3-172">Deploying an app to the HoloLens Emulator</span></span>

1. <span data-ttu-id="3cba3-173">Vergewissern Sie sich, dass Sie **[entweder den HoloLens 2- oder den HoloLens-Emulator (1. Generation) installiert haben](../install-the-tools.md#installation-checklist)**</span><span class="sxs-lookup"><span data-stu-id="3cba3-173">Make sure you've **[installed either the HoloLens 2 or HoloLens (1st gen) Emulator](../install-the-tools.md#installation-checklist)**</span></span>
2. <span data-ttu-id="3cba3-174">Wählen Sie Ihre Buildkonfiguration und den Emulator ausgehend von Ihrem Gerät aus.</span><span class="sxs-lookup"><span data-stu-id="3cba3-174">Select your build configuration and emulator based on your device</span></span>

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. <span data-ttu-id="3cba3-175">Sie können Ihre App ganz nach Ihren Anforderungen erstellen, bereitstellen und debuggen.</span><span class="sxs-lookup"><span data-stu-id="3cba3-175">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="3cba3-176">Wählen Sie **Debuggen > Debuggen starten** aus, um Ihre App bereitzustellen und den Debugvorgang zu starten.</span><span class="sxs-lookup"><span data-stu-id="3cba3-176">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="3cba3-177">Wählen Sie **Erstellen > Bereitstellen** aus, um eine Erstellung und Bereitstellung ohne Debuggen auszuführen.</span><span class="sxs-lookup"><span data-stu-id="3cba3-177">Select **Build > Deploy** to build and deploy without debuggingg</span></span>

![Starten ohne Debuggen in Visual Studio](images/deploywithdebugging.png)

## <a name="deploying-a-vr-app-to-your-local-pc"></a><span data-ttu-id="3cba3-179">Bereitstellen einer VR-App auf Ihrem lokalen PC</span><span class="sxs-lookup"><span data-stu-id="3cba3-179">Deploying a VR app to your Local PC</span></span> 

<span data-ttu-id="3cba3-180">Zum Verwenden eines immersiven Windows Mixed Reality-Headsets, das eine Verbindung mit Ihrem PC oder dem [Mixed Reality-Simulator](using-the-windows-mixed-reality-simulator.md) herstellt:</span><span class="sxs-lookup"><span data-stu-id="3cba3-180">To use a Windows Mixed Reality immersive headset that connects to your PC or the [Mixed Reality simulator](using-the-windows-mixed-reality-simulator.md):</span></span>
1. <span data-ttu-id="3cba3-181">Wählen Sie eine **x86**- oder **x64**-Buildkonfiguration aus</span><span class="sxs-lookup"><span data-stu-id="3cba3-181">Select an **x86** or **x64** build configuration for your app</span></span>
2. <span data-ttu-id="3cba3-182">Wählen Sie im Dropdownmenü für das Bereitstellungsziel **Lokaler Computer** aus</span><span class="sxs-lookup"><span data-stu-id="3cba3-182">Select **Local Machine** in the deployment target drop-down menu</span></span>
3. <span data-ttu-id="3cba3-183">Sie können Ihre App ganz nach Ihren Anforderungen erstellen, bereitstellen und debuggen.</span><span class="sxs-lookup"><span data-stu-id="3cba3-183">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="3cba3-184">Wählen Sie **Debuggen > Debuggen starten** aus, um Ihre App bereitzustellen und den Debugvorgang zu starten.</span><span class="sxs-lookup"><span data-stu-id="3cba3-184">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="3cba3-185">Wählen Sie **Erstellen > Bereitstellen** aus, um eine Erstellung und Bereitstellung ohne Debuggen auszuführen.</span><span class="sxs-lookup"><span data-stu-id="3cba3-185">Select **Build > Deploy** to build and deploy without debugging</span></span>

## <a name="pairing-your-device"></a><span data-ttu-id="3cba3-186">Koppeln Ihres Geräts</span><span class="sxs-lookup"><span data-stu-id="3cba3-186">Pairing your device</span></span>

<span data-ttu-id="3cba3-187">Beim erstmaligen Bereitstellen einer App aus Visual Studio in Ihrer HoloLens werden Sie zur Eingabe einer PIN aufgefordert.</span><span class="sxs-lookup"><span data-stu-id="3cba3-187">The first time you deploy an app from Visual Studio to your HoloLens, you'll be prompted for a PIN.</span></span> <span data-ttu-id="3cba3-188">Generieren Sie auf der HoloLens eine PIN, indem Sie die Einstellungs-App starten, zu **Update > Für Entwickler** navigieren und auf **Koppeln** tippen.</span><span class="sxs-lookup"><span data-stu-id="3cba3-188">On the HoloLens, generate a PIN by launching the Settings app, go to **Update > For Developers**, and tap on **Pair**.</span></span> <span data-ttu-id="3cba3-189">Wenn die PIN auf Ihrer HoloLens angezeigt wird, geben Sie sie in Visual Studio ein.</span><span class="sxs-lookup"><span data-stu-id="3cba3-189">When the PIN is displayed on your HoloLens, type it into Visual Studio.</span></span> <span data-ttu-id="3cba3-190">Tippen Sie nach dem vollzogenen Koppeln in Ihrer HoloLens auf **Fertig**, um das Dialogfeld zu schließen.</span><span class="sxs-lookup"><span data-stu-id="3cba3-190">After pairing is complete, tap **Done** on your HoloLens to dismiss the dialog.</span></span> <span data-ttu-id="3cba3-191">Dieser PC ist nun mit der HoloLens gekoppelt, und Sie können Apps automatisch bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="3cba3-191">This PC is now paired with the HoloLens and you can deploy apps automatically.</span></span> <span data-ttu-id="3cba3-192">Wiederholen Sie diese Schritte für jeden PC, der zum Bereitstellen von Apps auf Ihrer HoloLens verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="3cba3-192">Repeat these steps for every PC that's used to deploy apps to your HoloLens.</span></span>

<span data-ttu-id="3cba3-193">So heben Sie die Kopplung Ihrer HoloLens mit allen gekoppelten Computern auf:</span><span class="sxs-lookup"><span data-stu-id="3cba3-193">To unpair your HoloLens from all paired computers:</span></span>
* <span data-ttu-id="3cba3-194">Starten Sie die App **Einstellungen**, navigieren Sie zu **Aktualisieren > Für Entwickler**, und tippen Sie auf **Löschen**.</span><span class="sxs-lookup"><span data-stu-id="3cba3-194">Launch the **Settings** app, go to **Update > For Developers**, and tap on **Clear**.</span></span>

## <a name="graphics-debugger-for-hololens-1st-gen"></a><span data-ttu-id="3cba3-195">Grafikdebugger für HoloLens (1. Gen.)</span><span class="sxs-lookup"><span data-stu-id="3cba3-195">Graphics Debugger for HoloLens (1st gen)</span></span>

<span data-ttu-id="3cba3-196">Die Visual Studio-Grafikdiagnose-Tools sind beim Schreiben und Optimieren einer holografischen App nützlich.</span><span class="sxs-lookup"><span data-stu-id="3cba3-196">The Visual Studio Graphics Diagnostics tools are helpful when writing and optimizing a Holographic app.</span></span> <span data-ttu-id="3cba3-197">Ausführliche Informationen finden Sie unter [Visual Studio-Grafikdiagnose auf MSDN](/previous-versions/visualstudio/visual-studio-2015/debugger/visual-studio-graphics-diagnostics).</span><span class="sxs-lookup"><span data-stu-id="3cba3-197">See [Visual Studio Graphics Diagnostics on MSDN](/previous-versions/visualstudio/visual-studio-2015/debugger/visual-studio-graphics-diagnostics) for full details.</span></span>

<span data-ttu-id="3cba3-198">**So starten Sie den Grafikdebugger**</span><span class="sxs-lookup"><span data-stu-id="3cba3-198">**To Start the Graphics Debugger**</span></span>
1. <span data-ttu-id="3cba3-199">Befolgen Sie die Anweisungen oben, um ein Gerät oder einen Emulator als Ziel festzulegen.</span><span class="sxs-lookup"><span data-stu-id="3cba3-199">Follow the instructions above to target a device or emulator</span></span>
2. <span data-ttu-id="3cba3-200">Navigieren Sie zu **Debuggen > Grafik > Diagnose starten**</span><span class="sxs-lookup"><span data-stu-id="3cba3-200">Go to **Debug > Graphics > Start Diagnostics**</span></span>
3. <span data-ttu-id="3cba3-201">Wenn Sie die Diagnose zum ersten Mal auf einer HoloLens starten, wird möglicherweise ein Fehler „Zugriff verweigert“ angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3cba3-201">The first time you start diagnostics with a HoloLens, you may get an "access denied" error.</span></span> <span data-ttu-id="3cba3-202">Starten Sie die HoloLens neu, damit die aktualisierten Berechtigungen wirksam werden, und wiederholen Sie den Vorgang.</span><span class="sxs-lookup"><span data-stu-id="3cba3-202">Reboot your HoloLens to let the updated permissions take effect and try again.</span></span>

## <a name="profiling"></a><span data-ttu-id="3cba3-203">Profilerstellung</span><span class="sxs-lookup"><span data-stu-id="3cba3-203">Profiling</span></span>

<span data-ttu-id="3cba3-204">Die Visual Studio-Tools zur Profilerstellung ermöglichen Ihnen das Analysieren von Leistung und Ressourcennutzung Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="3cba3-204">The Visual Studio profiling tools allow you to analyze your app's performance and resource use.</span></span> <span data-ttu-id="3cba3-205">Dies beinhaltet Tools zur Optimierung von CPU-, Arbeitsspeicher-, Grafik- und Netzwerkauslastung.</span><span class="sxs-lookup"><span data-stu-id="3cba3-205">This includes tools to optimize CPU, memory, graphics, and network use.</span></span> <span data-ttu-id="3cba3-206">Ausführliche Informationen finden Sie unter [Ausführen von Diagnosetools ohne Debuggen auf MSDN](/previous-versions/visualstudio/visual-studio-2015/profiling/profiling-tools).</span><span class="sxs-lookup"><span data-stu-id="3cba3-206">See [Run diagnostic tools without debugging on MSDN](/previous-versions/visualstudio/visual-studio-2015/profiling/profiling-tools) for full details.</span></span>

<span data-ttu-id="3cba3-207">**So starten Sie die Profilerstellungstools in HoloLens**</span><span class="sxs-lookup"><span data-stu-id="3cba3-207">**To Start the Profiling Tools with HoloLens**</span></span>
1. <span data-ttu-id="3cba3-208">Befolgen Sie die Anweisungen oben, um ein Gerät oder einen Emulator als Ziel festzulegen.</span><span class="sxs-lookup"><span data-stu-id="3cba3-208">Follow the instructions above to target a device or emulator</span></span>
2. <span data-ttu-id="3cba3-209">Navigieren Sie zu **Debuggen > Diagnosetools ohne Debuggen starten...**</span><span class="sxs-lookup"><span data-stu-id="3cba3-209">Go to **Debug > Start Diagnostic Tools Without Debugging...**</span></span>
3. <span data-ttu-id="3cba3-210">Wählen Sie die Tools aus, die Sie verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="3cba3-210">Select the tools you want to use</span></span>
4. <span data-ttu-id="3cba3-211">Wählen Sie **Start** aus.</span><span class="sxs-lookup"><span data-stu-id="3cba3-211">Select **Start**</span></span>
5. <span data-ttu-id="3cba3-212">Wenn Sie die Diagnose zum ersten Mal auf einer HoloLens ohne Debuggen starten, wird möglicherweise ein Fehler „Zugriff verweigert“ angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3cba3-212">The first time you start diagnostics without debugging with a HoloLens, you may get an "access denied" error.</span></span> <span data-ttu-id="3cba3-213">Starten Sie die HoloLens neu, damit die aktualisierten Berechtigungen wirksam werden, und wiederholen Sie den Vorgang.</span><span class="sxs-lookup"><span data-stu-id="3cba3-213">Reboot your HoloLens to let the updated permissions take effect and try again.</span></span>

## <a name="debugging-an-installed-or-running-app"></a><span data-ttu-id="3cba3-214">Debuggen einer installierten oder aktuell laufenden App</span><span class="sxs-lookup"><span data-stu-id="3cba3-214">Debugging an installed or running app</span></span>

<span data-ttu-id="3cba3-215">Sie können Visual Studio verwenden, um eine installierte Universelle Windows-App zu debuggen, ohne sie aus einem Visual Studio-Projekt bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="3cba3-215">You can use Visual Studio to debug an installed Universal Windows app without deploying from a Visual Studio project.</span></span> <span data-ttu-id="3cba3-216">Dies ist nützlich, wenn Sie ein installiertes App-Paket oder eine App debuggen möchten, die bereits ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="3cba3-216">This is useful if you want to debug an installed app package or debug an app that's already running.</span></span>
1. <span data-ttu-id="3cba3-217">Navigieren Sie zu **Debuggen > Andere Debugziele > Installiertes App-Paket debuggen**</span><span class="sxs-lookup"><span data-stu-id="3cba3-217">Go to **Debug -> Other Debug Targets -> Debug Installed App Package**</span></span>
2. <span data-ttu-id="3cba3-218">Wählen Sie das Ziel **Remotecomputer** für HoloLens oder **Lokaler Computer** für immersive Headsets aus.</span><span class="sxs-lookup"><span data-stu-id="3cba3-218">Select the **Remote Machine** target for HoloLens or **Local Machine** for immersive headsets.</span></span>
3. <span data-ttu-id="3cba3-219">Geben Sie die **IP-Adresse** Ihres Geräts ein.</span><span class="sxs-lookup"><span data-stu-id="3cba3-219">Enter your device’s **IP address**</span></span>
4. <span data-ttu-id="3cba3-220">Wählen Sie den Authentifizierungsmodus **Universell** aus.</span><span class="sxs-lookup"><span data-stu-id="3cba3-220">Choose the **Universal** Authentication Mode</span></span>
5. <span data-ttu-id="3cba3-221">Im Fenster werden sowohl ausgeführte als auch inaktive Apps angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3cba3-221">The window shows both running and inactive apps.</span></span> <span data-ttu-id="3cba3-222">Suchen Sie die App aus, die Sie debuggen möchten.</span><span class="sxs-lookup"><span data-stu-id="3cba3-222">Pick the one what you’d like to debug.</span></span>
6. <span data-ttu-id="3cba3-223">Wählen Sie den zu debuggenden Codetyp aus (Verwaltet, Nativ, Gemischt)</span><span class="sxs-lookup"><span data-stu-id="3cba3-223">Choose the type of code to debug (Managed, Native, Mixed)</span></span>
7. <span data-ttu-id="3cba3-224">Wählen Sie **Anfügen** oder **Start** aus.</span><span class="sxs-lookup"><span data-stu-id="3cba3-224">Select **Attach** or **Start**</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="3cba3-225">Nächster Entwicklungsprüfpunkt</span><span class="sxs-lookup"><span data-stu-id="3cba3-225">Next Development Checkpoint</span></span>

<span data-ttu-id="3cba3-226">Wenn Sie dem Weg der Unity-Entwicklungsprüfpunkte folgen, den wir entworfen haben, befinden Sie sich in der Mitte der Bereitstellungsphase.</span><span class="sxs-lookup"><span data-stu-id="3cba3-226">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of the deployment stage.</span></span> <span data-ttu-id="3cba3-227">Von hier aus können Sie mit dem nächsten Thema fortfahren:</span><span class="sxs-lookup"><span data-stu-id="3cba3-227">From here, you can continue to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3cba3-228">Bereitstellen im HoloLens-Emulator</span><span class="sxs-lookup"><span data-stu-id="3cba3-228">Deploying to HoloLens emulator</span></span>](using-the-hololens-emulator.md)

<span data-ttu-id="3cba3-229">Oder fahren Sie direkt mit dem Hinzufügen erweiterter Dienste fort:</span><span class="sxs-lookup"><span data-stu-id="3cba3-229">Or jump directly to adding advanced services:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3cba3-230">Erweiterte Dienste</span><span class="sxs-lookup"><span data-stu-id="3cba3-230">Advanced services</span></span>](../../develop/unity/unity-development-overview.md#5-adding-services)

<span data-ttu-id="3cba3-231">Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="3cba3-231">You can always go back to the [Unity development checkpoints](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="3cba3-232">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="3cba3-232">See also</span></span>
* [<span data-ttu-id="3cba3-233">Installieren der Tools</span><span class="sxs-lookup"><span data-stu-id="3cba3-233">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="3cba3-234">Verwendung des HoloLens-Emulators</span><span class="sxs-lookup"><span data-stu-id="3cba3-234">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="3cba3-235">Bereitstellen und Debuggen von UWP (Universelle Windows-Plattform)-Apps</span><span class="sxs-lookup"><span data-stu-id="3cba3-235">Deploying and debugging Universal Windows Platform (UWP) apps</span></span>](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps)
* [<span data-ttu-id="3cba3-236">Aktivieren Ihres Geräts für die Entwicklung</span><span class="sxs-lookup"><span data-stu-id="3cba3-236">Enable your device for development</span></span>](/windows/uwp/get-started/enable-your-device-for-development)