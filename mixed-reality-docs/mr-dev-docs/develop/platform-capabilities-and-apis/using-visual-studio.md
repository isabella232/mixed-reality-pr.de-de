---
title: Verwenden von Visual Studio zum Bereitstellen und Debuggen
description: Erfahren Sie, wie Sie Apps für HoloLens und Windows Mixed Reality mithilfe von Visual Studio erstellen, debuggen und bereitstellen.
author: pbarnettms
ms.author: pbarnett
ms.date: 04/13/2020
ms.topic: article
ms.localizationpriority: high
keywords: Visual Studio, HoloLens, Mixed Reality, debuggen, bereitstellen
ms.openlocfilehash: 5510646c058f683babff5e9e34dd296f88cd06c3
ms.sourcegitcommit: b4bdac2c4d7315902712ce74fd909fb8383d4bfd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2021
ms.locfileid: "110543226"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a><span data-ttu-id="49241-104">Verwenden von Visual Studio zum Bereitstellen und Debuggen</span><span class="sxs-lookup"><span data-stu-id="49241-104">Using Visual Studio to deploy and debug</span></span>

<span data-ttu-id="49241-105">Unabhängig davon, ob Sie DirectX oder Unity zur Entwicklung ihrer Mixed Reality-App verwenden, Visual Studio ist Ihr Tool der Wahl zum Debuggen und Bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="49241-105">Whether you're using DirectX or Unity to develop your mixed reality app, Visual Studio is your go-to tool for debugging and deployment.</span></span> <span data-ttu-id="49241-106">In diesem Abschnitt wird Folgendes erläutert:</span><span class="sxs-lookup"><span data-stu-id="49241-106">In this section, you will learn how to:</span></span>
* <span data-ttu-id="49241-107">Bereitstellen von Anwendungen auf Ihrer HoloLens oder Ihrem immersiven Windows Mixed Reality-Headset mithilfe von Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="49241-107">Deploy applications to your HoloLens or Windows Mixed Reality immersive headset through Visual Studio.</span></span>
* <span data-ttu-id="49241-108">Verwenden des in Visual Studio integrierten HoloLens-Emulators.</span><span class="sxs-lookup"><span data-stu-id="49241-108">Use the HoloLens emulator built in to Visual Studio.</span></span>
* <span data-ttu-id="49241-109">Debuggen von Mixed Reality-Apps.</span><span class="sxs-lookup"><span data-stu-id="49241-109">Debug mixed reality apps.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="49241-110">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="49241-110">Prerequisites</span></span>

1. <span data-ttu-id="49241-111">Installationsanweisungen finden Sie unter [Installieren der Tools](../../develop/install-the-tools.md#installation-checklist).</span><span class="sxs-lookup"><span data-stu-id="49241-111">See [Install the Tools](../../develop/install-the-tools.md#installation-checklist) for installation instructions.</span></span>
2. <span data-ttu-id="49241-112">Erstellen Sie ein neues Projekt für Universelle Windows-Apps in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="49241-112">Create a new Universal Windows app project in Visual Studio.</span></span>  <span data-ttu-id="49241-113">Verwenden Sie für HoloLens (1. Gen.) Visual Studio 2017 oder höher.</span><span class="sxs-lookup"><span data-stu-id="49241-113">For HoloLens (1st gen), use Visual Studio 2017 or newer.</span></span>  <span data-ttu-id="49241-114">Verwenden Sie für HoloLens 2 Visual Studio 2019 16.2 oder höher.</span><span class="sxs-lookup"><span data-stu-id="49241-114">For HoloLens 2, use Visual Studio 2019 16.2 or newer.</span></span> <span data-ttu-id="49241-115">C# und C++ werden unterstützt.</span><span class="sxs-lookup"><span data-stu-id="49241-115">C# and C++ are supported.</span></span> <span data-ttu-id="49241-116">(Oder befolgen Sie die Anweisungen zum [Erstellen einer App in Unity](../../develop/unity/tutorials/holograms-100.md).)</span><span class="sxs-lookup"><span data-stu-id="49241-116">(Or follow the instructions to [create an app in Unity](../../develop/unity/tutorials/holograms-100.md).)</span></span>

## <a name="enabling-developer-mode"></a><span data-ttu-id="49241-117">Aktivieren des Entwicklermodus</span><span class="sxs-lookup"><span data-stu-id="49241-117">Enabling Developer Mode</span></span>

<span data-ttu-id="49241-118">Aktivieren Sie zunächst den **Entwicklermodus** auf Ihrem Gerät, damit Visual Studio eine Verbindung damit herstellen kann.</span><span class="sxs-lookup"><span data-stu-id="49241-118">Start by enabling **Developer Mode** on your device, so Visual Studio can connect to it.</span></span>

### <a name="hololens"></a><span data-ttu-id="49241-119">HoloLens</span><span class="sxs-lookup"><span data-stu-id="49241-119">HoloLens</span></span>

1. <span data-ttu-id="49241-120">Schalten Sie die HoloLens ein, und setzen Sie sie auf.</span><span class="sxs-lookup"><span data-stu-id="49241-120">Turn on your HoloLens and put on the device.</span></span>
2. <span data-ttu-id="49241-121">Verwenden Sie die [Startgeste](../../design/system-gesture.md), um das Hauptmenü zu starten.</span><span class="sxs-lookup"><span data-stu-id="49241-121">Use the [start gesture](../../design/system-gesture.md) to launch the main menu.</span></span>
3. <span data-ttu-id="49241-122">Wählen Sie die Kachel **Einstellungen** aus, um die App in Ihrer Umgebung zu starten.</span><span class="sxs-lookup"><span data-stu-id="49241-122">Select the **Settings** tile to launch the app in your environment.</span></span>
4. <span data-ttu-id="49241-123">Wählen Sie das Menüelement **Aktualisieren** aus.</span><span class="sxs-lookup"><span data-stu-id="49241-123">Select the **Update** menu item.</span></span>
5. <span data-ttu-id="49241-124">Wählen Sie das Menüelement **Für Entwickler** aus.</span><span class="sxs-lookup"><span data-stu-id="49241-124">Select the **For developers** menu item.</span></span>
6. <span data-ttu-id="49241-125">Aktivieren Sie **Use developer feature** (Entwicklerfunktion verwenden), um auf Ihrer HoloLens Apps aus Visual Studio bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="49241-125">Enable **Use developer features** to deploy apps from Visual Studio to your HoloLens.</span></span> <span data-ttu-id="49241-126">Wenn auf Ihrem Gerät Windows Holographic, Version 21H1 oder höher ausgeführt wird, aktivieren Sie außerdem **Device Discovery** (Geräteermittlung).</span><span class="sxs-lookup"><span data-stu-id="49241-126">If your device is running Windows Holographic version 21H1 or newer, also enable **Device discovery**.</span></span>
7. <span data-ttu-id="49241-127">Optional: Scrollen Sie nach unten, und aktivieren Sie auch das **Geräteportal**, mit dem Sie sich über einen Webbrowser mit dem [Windows-Geräteportal](using-the-windows-device-portal.md) auf Ihrer HoloLens verbinden können.</span><span class="sxs-lookup"><span data-stu-id="49241-127">Optional: Scroll down and also enable **Device Portal**, which lets you connect to the [Windows Device Portal](using-the-windows-device-portal.md) on your HoloLens from a web browser.</span></span>

### <a name="windows-pc"></a><span data-ttu-id="49241-128">Windows PC</span><span class="sxs-lookup"><span data-stu-id="49241-128">Windows PC</span></span>

<span data-ttu-id="49241-129">Wenn Sie mit einem Windows Mixed Reality-Headset arbeiten, das mit dem PC verbunden ist, müssen Sie den **Entwicklermodus** auf dem PC aktivieren.</span><span class="sxs-lookup"><span data-stu-id="49241-129">If you're working with a Windows Mixed Reality headset connected to your PC, you must enable **Developer Mode** on the PC.</span></span>
1. <span data-ttu-id="49241-130">Navigieren Sie zu **Einstellungen**</span><span class="sxs-lookup"><span data-stu-id="49241-130">Go to **Settings**</span></span>
2. <span data-ttu-id="49241-131">Wählen Sie **Update und Sicherheit** aus</span><span class="sxs-lookup"><span data-stu-id="49241-131">Select **Update and Security**</span></span>
3. <span data-ttu-id="49241-132">Wählen Sie **Für Entwickler** aus</span><span class="sxs-lookup"><span data-stu-id="49241-132">Select **For developers**</span></span>
4. <span data-ttu-id="49241-133">Aktivieren Sie den **Entwicklermodus**, lesen Sie den Haftungsausschluss für die ausgewählte Einstellung, und wählen Sie dann „Ja“ aus, um die Änderung zu übernehmen.</span><span class="sxs-lookup"><span data-stu-id="49241-133">Enable **Developer Mode**, read the disclaimer for the setting you chose, then select Yes to accept the change.</span></span>

## <a name="deploying-a-hololens-app-over-wi-fi"></a><span data-ttu-id="49241-134">Bereitstellen einer HoloLens-App über WLAN</span><span class="sxs-lookup"><span data-stu-id="49241-134">Deploying a HoloLens app over Wi-Fi</span></span> 

<span data-ttu-id="49241-135">Konfigurieren Sie Ihr Visual Studio-Projekt mit den folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="49241-135">Configure your Visual Studio project with the following properties:</span></span>

1. <span data-ttu-id="49241-136">Wählen Sie die Optionen für die Kompilierung von Apps aus</span><span class="sxs-lookup"><span data-stu-id="49241-136">Select your apps compilation options</span></span>
    * <span data-ttu-id="49241-137">Wählen Sie für Unity-Projekte entweder **Release** oder **Master** aus</span><span class="sxs-lookup"><span data-stu-id="49241-137">For Unity projects, choose either **Release** or **Master**</span></span> 
    * <span data-ttu-id="49241-138">Wählen Sie für alle anderen Projekte **Release** aus</span><span class="sxs-lookup"><span data-stu-id="49241-138">For all other projects, choose **Release**</span></span>

> [!NOTE]
> <span data-ttu-id="49241-139">Umfassende Definitionen für jede der Kompilierungsoptionen finden Sie unter [Exportieren und Entwickeln von Visual Studio-Projektmappen](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).</span><span class="sxs-lookup"><span data-stu-id="49241-139">You can find complete definitions for each compilation option in [exporting and building Visual Studio solutions](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).</span></span>

2. <span data-ttu-id="49241-140">Wählen Sie Ihre Buildkonfiguration ausgehend von Ihrem Gerät aus.</span><span class="sxs-lookup"><span data-stu-id="49241-140">Select your build configuration based on your device</span></span>

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. <span data-ttu-id="49241-141">Wählen Sie im Dropdownmenü für das Bereitstellungsziel **Remotecomputer** aus</span><span class="sxs-lookup"><span data-stu-id="49241-141">Select **Remote Machine** in the deployment target drop-down menu</span></span>

![Bereitstellungsziel „Remotecomputer“ in Visual Studio](images/remotemachinesetting_arm64.png)

<span data-ttu-id="49241-143">Als nächstes müssen Sie die Remoteverbindung festlegen.</span><span class="sxs-lookup"><span data-stu-id="49241-143">Next, you need to set your remote connection.</span></span> <span data-ttu-id="49241-144">Navigieren Sie für C++- und JavaScript-Projekte zu **Projekt > Eigenschaften > Konfigurationseigenschaften > Debuggen**.</span><span class="sxs-lookup"><span data-stu-id="49241-144">For C++ and JavaScript projects, go to **Project > Properties > Configuration Properties > Debugging**.</span></span> <span data-ttu-id="49241-145">Wenn Sie in einem C#-Projekt arbeiten, sollte automatisch ein Dialogfeld angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="49241-145">If you're working in a C# project, a dialog should automatically appear.</span></span>

> [!NOTE]
> <span data-ttu-id="49241-146">Wenn das Dialogfeld für die Remoteverbindung nicht in Ihrem C#-Projekt angezeigt wird, können Sie es manuell über **Eigenschaften > Debuggen** öffnen.</span><span class="sxs-lookup"><span data-stu-id="49241-146">If the remote connection dialog doesn't appear in your C# project, you can open it manually from **Properties > Debug**.</span></span>

1. <span data-ttu-id="49241-147">Geben Sie die IP-Adresse Ihres Geräts im Feld **Adresse** oder **Computername** ein.</span><span class="sxs-lookup"><span data-stu-id="49241-147">Enter the IP address of your device in the **Address** or **Machine Name** field.</span></span> 
    * <span data-ttu-id="49241-148">Sie finden die IP-Adresse Ihrer HoloLens unter **Einstellungen > Netzwerk und Internet > Erweiterte Optionen**</span><span class="sxs-lookup"><span data-stu-id="49241-148">You can find the IP address on your HoloLens under **Settings > Network & Internet > Advanced Options**</span></span>
    * <span data-ttu-id="49241-149">Wir empfehlen, die IP-Adresse immer manuell einzugeben, statt sich auf die Funktion zur automatischen Erkennung zu verlassen.</span><span class="sxs-lookup"><span data-stu-id="49241-149">We always recommend manually entering your IP address rather than depending on the Auto Detected feature</span></span>

2. <span data-ttu-id="49241-150">Legen Sie den **Authentifizierungsmodus** auf **Universell (Unverschlüsseltes Protokoll)** fest.</span><span class="sxs-lookup"><span data-stu-id="49241-150">Set the **Authentication Mode** to **Universal (Unencrypted protocol)**</span></span>

  ![Dialogfeld „Remoteverbindung“ in Visual Studio](images/remotedeploy.png)

3. <span data-ttu-id="49241-152">Sie können Ihre App ganz nach Ihren Anforderungen erstellen, bereitstellen und debuggen.</span><span class="sxs-lookup"><span data-stu-id="49241-152">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="49241-153">Wählen Sie **Debuggen > Debuggen starten** aus, um Ihre App bereitzustellen und den Debugvorgang zu starten.</span><span class="sxs-lookup"><span data-stu-id="49241-153">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="49241-154">Wählen Sie **Erstellen > Bereitstellen** aus, um eine Erstellung und Bereitstellung ohne Debuggen auszuführen.</span><span class="sxs-lookup"><span data-stu-id="49241-154">Select **Build > Deploy** to build and deploy without debugging</span></span>

![Starten ohne Debuggen in Visual Studio](images/deploywithdebugging.png)

4. <span data-ttu-id="49241-156">Beim erstmaligen Bereitstellen einer App in Ihrer HoloLens von Ihrem Computer aus werden Sie zur Eingabe einer PIN aufgefordert.</span><span class="sxs-lookup"><span data-stu-id="49241-156">The first time you deploy an app to your HoloLens from your PC, you'll be prompted for a PIN.</span></span> <span data-ttu-id="49241-157">Befolgen Sie die Anweisungen unten zum **Koppeln Ihres Geräts**.</span><span class="sxs-lookup"><span data-stu-id="49241-157">Follow the **Pairing your device** instructions below.</span></span>

## <a name="deploying-a-hololens-app-over-usb"></a><span data-ttu-id="49241-158">Bereitstellen einer HoloLens-App über USB</span><span class="sxs-lookup"><span data-stu-id="49241-158">Deploying a HoloLens app over USB</span></span> 

<br>

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Deploying-your-HoloLens-2-application/player?format=ny]

1. <span data-ttu-id="49241-159">Wählen Sie die Optionen für die Kompilierung von Apps aus</span><span class="sxs-lookup"><span data-stu-id="49241-159">Select your apps compilation options</span></span>
    * <span data-ttu-id="49241-160">Wählen Sie für Unity-Projekte entweder **Release** oder **Master** aus</span><span class="sxs-lookup"><span data-stu-id="49241-160">For Unity projects, choose either **Release** or **Master**</span></span> 
    * <span data-ttu-id="49241-161">Wählen Sie für alle anderen Projekte **Release** aus</span><span class="sxs-lookup"><span data-stu-id="49241-161">For all other projects, choose **Release**</span></span>

> [!NOTE]
> <span data-ttu-id="49241-162">Umfassende Definitionen für jede der Kompilierungsoptionen finden Sie unter [Exportieren und Entwickeln von Visual Studio-Projektmappen](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).</span><span class="sxs-lookup"><span data-stu-id="49241-162">You can find complete definitions for each compilation option in [exporting and building Visual Studio solutions](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).</span></span>

2. <span data-ttu-id="49241-163">Wählen Sie Ihre Buildkonfiguration ausgehend von Ihrem Gerät aus.</span><span class="sxs-lookup"><span data-stu-id="49241-163">Select your build configuration based on your device</span></span>

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. <span data-ttu-id="49241-164">Wählen Sie im Dropdownmenü für das Bereitstellungsziel **Gerät** aus</span><span class="sxs-lookup"><span data-stu-id="49241-164">Select **Device** in the deployment target drop-down menu</span></span>

![Gerätebereitstellung in Visual Studio](images/buildsettingsusbdeploy_arm64.png)

4. <span data-ttu-id="49241-166">Sie können Ihre App ganz nach Ihren Anforderungen erstellen, bereitstellen und debuggen.</span><span class="sxs-lookup"><span data-stu-id="49241-166">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="49241-167">Wählen Sie **Debuggen > Debuggen starten** aus, um Ihre App bereitzustellen und den Debugvorgang zu starten.</span><span class="sxs-lookup"><span data-stu-id="49241-167">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="49241-168">Wählen Sie **Erstellen > Bereitstellen** aus, um eine Erstellung und Bereitstellung ohne Debuggen auszuführen.</span><span class="sxs-lookup"><span data-stu-id="49241-168">Select **Build > Deploy** to build and deploy without debugging</span></span>

![Starten ohne Debuggen in Visual Studio](images/deploywithdebugging.png)</br>

5. <span data-ttu-id="49241-170">Beim erstmaligen Bereitstellen einer App in Ihrer HoloLens von Ihrem Computer aus werden Sie zur Eingabe einer PIN aufgefordert.</span><span class="sxs-lookup"><span data-stu-id="49241-170">The first time you deploy an app to your HoloLens from your PC, you'll be prompted for a PIN.</span></span> <span data-ttu-id="49241-171">Befolgen Sie die Anweisungen unten zum **Koppeln Ihres Geräts**.</span><span class="sxs-lookup"><span data-stu-id="49241-171">Follow the **Pairing your device** instructions below.</span></span>

> [!NOTE]
> <span data-ttu-id="49241-172">Wenn Sie bei der Bereitstellung Ihrer Apps über USB eine beträchtliche Verzögerung feststellen, empfehlen wir, die [Anweisungen für Remotecomputer](#deploying-a-hololens-app-over-wi-fi) im vorhergehenden Abschnitt umzusetzen.</span><span class="sxs-lookup"><span data-stu-id="49241-172">If you're seeing considerable lag time with your apps deployment over USB, we recommend using the [remote machine instructions](#deploying-a-hololens-app-over-wi-fi) in the previous section.</span></span>

## <a name="deploying-an-app-to-the-hololens-emulator"></a><span data-ttu-id="49241-173">Bereitstellen einer App auf dem HoloLens-Emulator</span><span class="sxs-lookup"><span data-stu-id="49241-173">Deploying an app to the HoloLens Emulator</span></span>

1. <span data-ttu-id="49241-174">Vergewissern Sie sich, dass Sie **[entweder den HoloLens 2- oder den HoloLens-Emulator (1. Generation) installiert haben](../install-the-tools.md#installation-checklist)**</span><span class="sxs-lookup"><span data-stu-id="49241-174">Make sure you've **[installed either the HoloLens 2 or HoloLens (1st gen) Emulator](../install-the-tools.md#installation-checklist)**</span></span>
2. <span data-ttu-id="49241-175">Wählen Sie Ihre Buildkonfiguration und den Emulator ausgehend von Ihrem Gerät aus.</span><span class="sxs-lookup"><span data-stu-id="49241-175">Select your build configuration and emulator based on your device</span></span>

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. <span data-ttu-id="49241-176">Sie können Ihre App ganz nach Ihren Anforderungen erstellen, bereitstellen und debuggen.</span><span class="sxs-lookup"><span data-stu-id="49241-176">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="49241-177">Wählen Sie **Debuggen > Debuggen starten** aus, um Ihre App bereitzustellen und den Debugvorgang zu starten.</span><span class="sxs-lookup"><span data-stu-id="49241-177">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="49241-178">Wählen Sie **Erstellen > Bereitstellen** aus, um eine Erstellung und Bereitstellung ohne Debuggen auszuführen.</span><span class="sxs-lookup"><span data-stu-id="49241-178">Select **Build > Deploy** to build and deploy without debuggingg</span></span>

![Starten ohne Debuggen in Visual Studio](images/deploywithdebugging.png)

## <a name="deploying-a-vr-app-to-your-local-pc"></a><span data-ttu-id="49241-180">Bereitstellen einer VR-App auf Ihrem lokalen PC</span><span class="sxs-lookup"><span data-stu-id="49241-180">Deploying a VR app to your Local PC</span></span> 

<span data-ttu-id="49241-181">Zum Verwenden eines immersiven Windows Mixed Reality-Headsets, das eine Verbindung mit Ihrem PC oder dem [Mixed Reality-Simulator](using-the-windows-mixed-reality-simulator.md) herstellt:</span><span class="sxs-lookup"><span data-stu-id="49241-181">To use a Windows Mixed Reality immersive headset that connects to your PC or the [Mixed Reality simulator](using-the-windows-mixed-reality-simulator.md):</span></span>
1. <span data-ttu-id="49241-182">Wählen Sie eine **x86**- oder **x64**-Buildkonfiguration aus</span><span class="sxs-lookup"><span data-stu-id="49241-182">Select an **x86** or **x64** build configuration for your app</span></span>
2. <span data-ttu-id="49241-183">Wählen Sie im Dropdownmenü für das Bereitstellungsziel **Lokaler Computer** aus</span><span class="sxs-lookup"><span data-stu-id="49241-183">Select **Local Machine** in the deployment target drop-down menu</span></span>
3. <span data-ttu-id="49241-184">Sie können Ihre App ganz nach Ihren Anforderungen erstellen, bereitstellen und debuggen.</span><span class="sxs-lookup"><span data-stu-id="49241-184">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="49241-185">Wählen Sie **Debuggen > Debuggen starten** aus, um Ihre App bereitzustellen und den Debugvorgang zu starten.</span><span class="sxs-lookup"><span data-stu-id="49241-185">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="49241-186">Wählen Sie **Erstellen > Bereitstellen** aus, um eine Erstellung und Bereitstellung ohne Debuggen auszuführen.</span><span class="sxs-lookup"><span data-stu-id="49241-186">Select **Build > Deploy** to build and deploy without debugging</span></span>

## <a name="pairing-your-device"></a><span data-ttu-id="49241-187">Koppeln Ihres Geräts</span><span class="sxs-lookup"><span data-stu-id="49241-187">Pairing your device</span></span>

<span data-ttu-id="49241-188">Beim erstmaligen Bereitstellen einer App aus Visual Studio in Ihrer HoloLens werden Sie zur Eingabe einer PIN aufgefordert.</span><span class="sxs-lookup"><span data-stu-id="49241-188">The first time you deploy an app from Visual Studio to your HoloLens, you'll be prompted for a PIN.</span></span> <span data-ttu-id="49241-189">Generieren Sie auf der HoloLens eine PIN, indem Sie die Einstellungs-App starten, zu **Update > Für Entwickler** navigieren und auf **Koppeln** tippen.</span><span class="sxs-lookup"><span data-stu-id="49241-189">On the HoloLens, generate a PIN by launching the Settings app, go to **Update > For Developers**, and tap on **Pair**.</span></span> <span data-ttu-id="49241-190">Wenn die PIN auf Ihrer HoloLens angezeigt wird, geben Sie sie in Visual Studio ein.</span><span class="sxs-lookup"><span data-stu-id="49241-190">When the PIN is displayed on your HoloLens, type it into Visual Studio.</span></span> <span data-ttu-id="49241-191">Tippen Sie nach dem vollzogenen Koppeln in Ihrer HoloLens auf **Fertig**, um das Dialogfeld zu schließen.</span><span class="sxs-lookup"><span data-stu-id="49241-191">After pairing is complete, tap **Done** on your HoloLens to dismiss the dialog.</span></span> <span data-ttu-id="49241-192">Dieser PC ist nun mit der HoloLens gekoppelt, und Sie können Apps automatisch bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="49241-192">This PC is now paired with the HoloLens and you can deploy apps automatically.</span></span> <span data-ttu-id="49241-193">Wiederholen Sie diese Schritte für jeden PC, der zum Bereitstellen von Apps auf Ihrer HoloLens verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="49241-193">Repeat these steps for every PC that's used to deploy apps to your HoloLens.</span></span>

<span data-ttu-id="49241-194">So heben Sie die Kopplung Ihrer HoloLens mit allen gekoppelten Computern auf:</span><span class="sxs-lookup"><span data-stu-id="49241-194">To unpair your HoloLens from all paired computers:</span></span>
* <span data-ttu-id="49241-195">Starten Sie die App **Einstellungen**, navigieren Sie zu **Aktualisieren > Für Entwickler**, und tippen Sie auf **Löschen**.</span><span class="sxs-lookup"><span data-stu-id="49241-195">Launch the **Settings** app, go to **Update > For Developers**, and tap on **Clear**.</span></span>

## <a name="graphics-debugger-for-hololens-1st-gen"></a><span data-ttu-id="49241-196">Grafikdebugger für HoloLens (1. Gen.)</span><span class="sxs-lookup"><span data-stu-id="49241-196">Graphics Debugger for HoloLens (1st gen)</span></span>

<span data-ttu-id="49241-197">Die Visual Studio-Grafikdiagnose-Tools sind beim Schreiben und Optimieren einer holografischen App nützlich.</span><span class="sxs-lookup"><span data-stu-id="49241-197">The Visual Studio Graphics Diagnostics tools are helpful when writing and optimizing a Holographic app.</span></span> <span data-ttu-id="49241-198">Ausführliche Informationen finden Sie unter [Visual Studio-Grafikdiagnose auf MSDN](/previous-versions/visualstudio/visual-studio-2015/debugger/visual-studio-graphics-diagnostics).</span><span class="sxs-lookup"><span data-stu-id="49241-198">See [Visual Studio Graphics Diagnostics on MSDN](/previous-versions/visualstudio/visual-studio-2015/debugger/visual-studio-graphics-diagnostics) for full details.</span></span>

<span data-ttu-id="49241-199">**So starten Sie den Grafikdebugger**</span><span class="sxs-lookup"><span data-stu-id="49241-199">**To Start the Graphics Debugger**</span></span>
1. <span data-ttu-id="49241-200">Befolgen Sie die Anweisungen oben, um ein Gerät oder einen Emulator als Ziel festzulegen.</span><span class="sxs-lookup"><span data-stu-id="49241-200">Follow the instructions above to target a device or emulator</span></span>
2. <span data-ttu-id="49241-201">Navigieren Sie zu **Debuggen > Grafik > Diagnose starten**</span><span class="sxs-lookup"><span data-stu-id="49241-201">Go to **Debug > Graphics > Start Diagnostics**</span></span>
3. <span data-ttu-id="49241-202">Wenn Sie die Diagnose zum ersten Mal auf einer HoloLens starten, wird möglicherweise ein Fehler „Zugriff verweigert“ angezeigt.</span><span class="sxs-lookup"><span data-stu-id="49241-202">The first time you start diagnostics with a HoloLens, you may get an "access denied" error.</span></span> <span data-ttu-id="49241-203">Starten Sie die HoloLens neu, damit die aktualisierten Berechtigungen wirksam werden, und wiederholen Sie den Vorgang.</span><span class="sxs-lookup"><span data-stu-id="49241-203">Reboot your HoloLens to let the updated permissions take effect and try again.</span></span>

## <a name="profiling"></a><span data-ttu-id="49241-204">Profilerstellung</span><span class="sxs-lookup"><span data-stu-id="49241-204">Profiling</span></span>

<span data-ttu-id="49241-205">Die Visual Studio-Tools zur Profilerstellung ermöglichen Ihnen das Analysieren von Leistung und Ressourcennutzung Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="49241-205">The Visual Studio profiling tools allow you to analyze your app's performance and resource use.</span></span> <span data-ttu-id="49241-206">Dies beinhaltet Tools zur Optimierung von CPU-, Arbeitsspeicher-, Grafik- und Netzwerkauslastung.</span><span class="sxs-lookup"><span data-stu-id="49241-206">This includes tools to optimize CPU, memory, graphics, and network use.</span></span> <span data-ttu-id="49241-207">Ausführliche Informationen finden Sie unter [Ausführen von Diagnosetools ohne Debuggen auf MSDN](/previous-versions/visualstudio/visual-studio-2015/profiling/profiling-tools).</span><span class="sxs-lookup"><span data-stu-id="49241-207">See [Run diagnostic tools without debugging on MSDN](/previous-versions/visualstudio/visual-studio-2015/profiling/profiling-tools) for full details.</span></span>

<span data-ttu-id="49241-208">**So starten Sie die Profilerstellungstools in HoloLens**</span><span class="sxs-lookup"><span data-stu-id="49241-208">**To Start the Profiling Tools with HoloLens**</span></span>
1. <span data-ttu-id="49241-209">Befolgen Sie die Anweisungen oben, um ein Gerät oder einen Emulator als Ziel festzulegen.</span><span class="sxs-lookup"><span data-stu-id="49241-209">Follow the instructions above to target a device or emulator</span></span>
2. <span data-ttu-id="49241-210">Navigieren Sie zu **Debuggen > Diagnosetools ohne Debuggen starten...**</span><span class="sxs-lookup"><span data-stu-id="49241-210">Go to **Debug > Start Diagnostic Tools Without Debugging...**</span></span>
3. <span data-ttu-id="49241-211">Wählen Sie die Tools aus, die Sie verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="49241-211">Select the tools you want to use</span></span>
4. <span data-ttu-id="49241-212">Wählen Sie **Start** aus.</span><span class="sxs-lookup"><span data-stu-id="49241-212">Select **Start**</span></span>
5. <span data-ttu-id="49241-213">Wenn Sie die Diagnose zum ersten Mal auf einer HoloLens ohne Debuggen starten, wird möglicherweise ein Fehler „Zugriff verweigert“ angezeigt.</span><span class="sxs-lookup"><span data-stu-id="49241-213">The first time you start diagnostics without debugging with a HoloLens, you may get an "access denied" error.</span></span> <span data-ttu-id="49241-214">Starten Sie die HoloLens neu, damit die aktualisierten Berechtigungen wirksam werden, und wiederholen Sie den Vorgang.</span><span class="sxs-lookup"><span data-stu-id="49241-214">Reboot your HoloLens to let the updated permissions take effect and try again.</span></span>

## <a name="debugging-an-installed-or-running-app"></a><span data-ttu-id="49241-215">Debuggen einer installierten oder aktuell laufenden App</span><span class="sxs-lookup"><span data-stu-id="49241-215">Debugging an installed or running app</span></span>

<span data-ttu-id="49241-216">Sie können Visual Studio verwenden, um eine installierte Universelle Windows-App zu debuggen, ohne sie aus einem Visual Studio-Projekt bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="49241-216">You can use Visual Studio to debug an installed Universal Windows app without deploying from a Visual Studio project.</span></span> <span data-ttu-id="49241-217">Dies ist nützlich, wenn Sie ein installiertes App-Paket oder eine App debuggen möchten, die bereits ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="49241-217">This is useful if you want to debug an installed app package or debug an app that's already running.</span></span>
1. <span data-ttu-id="49241-218">Navigieren Sie zu **Debuggen > Andere Debugziele > Installiertes App-Paket debuggen**</span><span class="sxs-lookup"><span data-stu-id="49241-218">Go to **Debug -> Other Debug Targets -> Debug Installed App Package**</span></span>
2. <span data-ttu-id="49241-219">Wählen Sie das Ziel **Remotecomputer** für HoloLens oder **Lokaler Computer** für immersive Headsets aus.</span><span class="sxs-lookup"><span data-stu-id="49241-219">Select the **Remote Machine** target for HoloLens or **Local Machine** for immersive headsets.</span></span>
3. <span data-ttu-id="49241-220">Geben Sie die **IP-Adresse** Ihres Geräts ein.</span><span class="sxs-lookup"><span data-stu-id="49241-220">Enter your device’s **IP address**</span></span>
4. <span data-ttu-id="49241-221">Wählen Sie den Authentifizierungsmodus **Universell** aus.</span><span class="sxs-lookup"><span data-stu-id="49241-221">Choose the **Universal** Authentication Mode</span></span>
5. <span data-ttu-id="49241-222">Im Fenster werden sowohl ausgeführte als auch inaktive Apps angezeigt.</span><span class="sxs-lookup"><span data-stu-id="49241-222">The window shows both running and inactive apps.</span></span> <span data-ttu-id="49241-223">Suchen Sie die App aus, die Sie debuggen möchten.</span><span class="sxs-lookup"><span data-stu-id="49241-223">Pick the one what you’d like to debug.</span></span>
6. <span data-ttu-id="49241-224">Wählen Sie den zu debuggenden Codetyp aus (Verwaltet, Nativ, Gemischt)</span><span class="sxs-lookup"><span data-stu-id="49241-224">Choose the type of code to debug (Managed, Native, Mixed)</span></span>
7. <span data-ttu-id="49241-225">Wählen Sie **Anfügen** oder **Start** aus.</span><span class="sxs-lookup"><span data-stu-id="49241-225">Select **Attach** or **Start**</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="49241-226">Nächster Entwicklungsprüfpunkt</span><span class="sxs-lookup"><span data-stu-id="49241-226">Next Development Checkpoint</span></span>

<span data-ttu-id="49241-227">Wenn Sie dem Weg der Unity-Entwicklungsprüfpunkte folgen, den wir entworfen haben, befinden Sie sich in der Mitte der Bereitstellungsphase.</span><span class="sxs-lookup"><span data-stu-id="49241-227">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of the deployment stage.</span></span> <span data-ttu-id="49241-228">Von hier aus können Sie mit dem nächsten Thema fortfahren:</span><span class="sxs-lookup"><span data-stu-id="49241-228">From here, you can continue to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="49241-229">Bereitstellen im HoloLens-Emulator</span><span class="sxs-lookup"><span data-stu-id="49241-229">Deploying to HoloLens emulator</span></span>](using-the-hololens-emulator.md)

<span data-ttu-id="49241-230">Oder fahren Sie direkt mit dem Hinzufügen erweiterter Dienste fort:</span><span class="sxs-lookup"><span data-stu-id="49241-230">Or jump directly to adding advanced services:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="49241-231">Erweiterte Dienste</span><span class="sxs-lookup"><span data-stu-id="49241-231">Advanced services</span></span>](../../develop/unity/unity-development-overview.md#5-adding-services)

<span data-ttu-id="49241-232">Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="49241-232">You can always go back to the [Unity development checkpoints](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="49241-233">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="49241-233">See also</span></span>
* [<span data-ttu-id="49241-234">Installieren der Tools</span><span class="sxs-lookup"><span data-stu-id="49241-234">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="49241-235">Verwendung des HoloLens-Emulators</span><span class="sxs-lookup"><span data-stu-id="49241-235">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="49241-236">Bereitstellen und Debuggen von UWP (Universelle Windows-Plattform)-Apps</span><span class="sxs-lookup"><span data-stu-id="49241-236">Deploying and debugging Universal Windows Platform (UWP) apps</span></span>](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps)
* [<span data-ttu-id="49241-237">Aktivieren Ihres Geräts für die Entwicklung</span><span class="sxs-lookup"><span data-stu-id="49241-237">Enable your device for development</span></span>](/windows/uwp/get-started/enable-your-device-for-development)
