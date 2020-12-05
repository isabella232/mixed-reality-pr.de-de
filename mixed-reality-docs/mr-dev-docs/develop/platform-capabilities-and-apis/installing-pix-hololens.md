---
title: Installieren von Pix für hololens 2
description: Erfahren Sie, wie Sie pix für hololens 2-Geräte installieren.
author: hferrone
ms.author: flbagar
ms.date: 12/02/2020
ms.topic: article
keywords: Hololens, hololens 2, pix, Capture, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 4554600414784b2644006e6e891f16f8ce3a79f5
ms.sourcegitcommit: 924f8c1ceb93c378f800cf88d82944cf80f092bc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2020
ms.locfileid: "96615364"
---
# <a name="installing-pix-for-hololens-2"></a><span data-ttu-id="f8529-104">Installieren von Pix für hololens 2</span><span class="sxs-lookup"><span data-stu-id="f8529-104">Installing PIX for HoloLens 2</span></span>

<span data-ttu-id="f8529-105">[Pix](https://devblogs.microsoft.com/pix) ist ein Tool zur Leistungsoptimierung und-Debuggen für DirectX 12-Anwendungen unter Windows.</span><span class="sxs-lookup"><span data-stu-id="f8529-105">[PIX](https://devblogs.microsoft.com/pix) is a performance tuning and debugging tool for DirectX 12 applications on Windows.</span></span> 

## <a name="setup"></a><span data-ttu-id="f8529-106">Einrichten</span><span class="sxs-lookup"><span data-stu-id="f8529-106">Setup</span></span>

1. <span data-ttu-id="f8529-107">Holen Sie sich die neueste pix- [Version]( https://devblogs.microsoft.com/pix/download) von Ihrem Host-PC, und verbinden Sie Ihre hololens 2 über ein USB-Kabel mit Ihrem PC.</span><span class="sxs-lookup"><span data-stu-id="f8529-107">Grab the latest PIX [release]( https://devblogs.microsoft.com/pix/download) from your host PC and connect your HoloLens 2 to your PC via a USB cable.</span></span>

2. <span data-ttu-id="f8529-108">Wenn sich Ihre hololens 2 in einem [Windows Insider-Build](https://insider.windows.com) befinden oder über eine Konfiguration verfügen, bei der PIX unterbrochen wird, müssen  [Sie Ihr Gerät erneut](https://docs.microsoft.com/hololens/hololens-recovery) löschen, um alle Daten zu löschen.</span><span class="sxs-lookup"><span data-stu-id="f8529-108">If your HoloLens 2 is on a [Windows Insider build](https://insider.windows.com) or has a configuration that breaks PIX,  [re-flash your device](https://docs.microsoft.com/hololens/hololens-recovery) to erase all data.</span></span>

3. <span data-ttu-id="f8529-109">**Entwicklermodus** und **Geräte Portal** aktivieren:</span><span class="sxs-lookup"><span data-stu-id="f8529-109">Enable **Developer Mode** and **Device Portal**:</span></span>

* <span data-ttu-id="f8529-110">Öffnen Sie die **Einstellungen** in der Shell:</span><span class="sxs-lookup"><span data-stu-id="f8529-110">Open **Settings** from Shell:</span></span>

![Screenshot des Menüs "hololens" mit hervorgehobener Einstellungs Schaltfläche](images/pix-img-01.jpg)

* <span data-ttu-id="f8529-112">Wählen Sie **Update & Sicherheit**:</span><span class="sxs-lookup"><span data-stu-id="f8529-112">Select **Update & Security**:</span></span>

![Screenshot des Fensters "Einstellungen" in hololens mit hervorgehobener Schaltfläche "aktualisieren und Sicherheit"](images/pix-img-02.jpg)

* <span data-ttu-id="f8529-114">Klicken Sie **für Entwickler**:</span><span class="sxs-lookup"><span data-stu-id="f8529-114">Click **For Developers**:</span></span>

![Screenshot der Schaltfläche "Sicherheit und Updates" mit hervorgehobener Schaltfläche "Entwickler"](images/pix-img-03.jpg)

* <span data-ttu-id="f8529-116">Aktivieren der **Verwendung von Entwickler Features** und **Aktivieren des Geräte Portals**</span><span class="sxs-lookup"><span data-stu-id="f8529-116">Turn on **Use Developer Features** and **Enable Device Portal**</span></span>

![Screenshot des Fensters "Entwickler" in den Einstellungen "Geräte Portal aktivieren"](images/pix-img-04.jpg)

![Screenshot des Fensters "Entwickler" in "Einstellungen" mit der Schaltfläche "entwickeln von Features umschalten"](images/pix-img-05.jpg)

* <span data-ttu-id="f8529-119">Starten Sie Visual Studio, wenn das Gerät immer noch verbunden ist, aktiv ist und der Benutzer angemeldet ist.</span><span class="sxs-lookup"><span data-stu-id="f8529-119">With the device still connected, awake, and with the user logged in, launch Visual Studio.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f8529-120">Stellen Sie sicher, dass sich Ihr Gerät nicht im Standbymodus befindet oder nicht</span><span class="sxs-lookup"><span data-stu-id="f8529-120">Make sure your device isn't in standby mode or asleep.</span></span> <span data-ttu-id="f8529-121">Wenn Sie Probleme mit diesem Schritt haben, finden Sie die [Anweisungen im Windows-Geräte Portal](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal).</span><span class="sxs-lookup"><span data-stu-id="f8529-121">If you're having trouble with this step, refer to the [Windows Device Portal instructions](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal).</span></span>

## <a name="preparing-for-deployment"></a><span data-ttu-id="f8529-122">Vorbereiten der Bereitstellung</span><span class="sxs-lookup"><span data-stu-id="f8529-122">Preparing for deployment</span></span>

1. <span data-ttu-id="f8529-123">Legen Sie in Visual Studio **ARM64** als Plattform und **Gerät** als Gerät fest:</span><span class="sxs-lookup"><span data-stu-id="f8529-123">In Visual Studio, set **ARM64** as the platform and **Device** as the device:</span></span>

![Screenshot der Visual Studio-Projekt Mappe mit hervorgehobenen Plattform-und Geräteeinstellungen](images/pix-img-06.png)

2. <span data-ttu-id="f8529-125">Wenn Sie von Visual Studio aufgefordert werden, eine **Pin** vom Gerät einzugeben:</span><span class="sxs-lookup"><span data-stu-id="f8529-125">When Visual Studio prompts you for a **PIN** from the device:</span></span>

![Screenshot der Visual Studio-Popup-Aufforderung zur PIN](images/pix-img-07.png)

* <span data-ttu-id="f8529-127">Auswählen von **Einstellungen** aus der Shell</span><span class="sxs-lookup"><span data-stu-id="f8529-127">Select **Settings** from Shell</span></span>
* <span data-ttu-id="f8529-128">Wählen Sie **Update & Sicherheit** aus.</span><span class="sxs-lookup"><span data-stu-id="f8529-128">Select **Update & Security**</span></span>
* <span data-ttu-id="f8529-129">Klicken Sie **für Entwickler** , und drücken Sie unter **Geräte** Ermittlung das Paar.</span><span class="sxs-lookup"><span data-stu-id="f8529-129">Click **For Developers** and press Pair under **Device Discovery**</span></span> 

![Screenshot von für Entwickler Fenster "in Einstellungen öffnen" mit hervorgehobener Geräte Ermittlung](images/pix-img-08.jpg)

![Screenshot des Popups für kostenpflichtige Geräte mit hervorgehobenem Registrierungscode](images/pix-img-09.jpg)

* <span data-ttu-id="f8529-132">Geben Sie die generierte PIN-Nummer in Visual Studio ein.</span><span class="sxs-lookup"><span data-stu-id="f8529-132">Enter the generated PIN number in Visual Studio</span></span>

3. <span data-ttu-id="f8529-133">Visual Studio stellt die app in den verbundenen hololens 2 bereit. Dies kann je nach App einige Minuten dauern.</span><span class="sxs-lookup"><span data-stu-id="f8529-133">Visual Studio will deploy the app to the connected HoloLens 2, which may take a few minutes depending on the app.</span></span>

## <a name="launching-pix"></a><span data-ttu-id="f8529-134">Starten von Pix</span><span class="sxs-lookup"><span data-stu-id="f8529-134">Launching PIX</span></span>

<span data-ttu-id="f8529-135">Überprüfen Sie zunächst mithilfe des Geräte Portals, ob die APP auf den hololens 2 ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="f8529-135">First, use Device Portal to verify the app is not running on the HoloLens 2.</span></span> <span data-ttu-id="f8529-136">Starten Sie dann pix, verbinden Sie sich mit Ihrem Gerät, und klicken Sie auf **Startseite**:</span><span class="sxs-lookup"><span data-stu-id="f8529-136">Then, launch PIX, connect to your device, and click **Home**:</span></span>

![Screenshot des pix-Anwendungs-Startbildschirms](images/pix-img-10.png)

* <span data-ttu-id="f8529-138">Wählen Sie im Menü auf der linken Seite die Option **verbinden** aus:</span><span class="sxs-lookup"><span data-stu-id="f8529-138">Select **Connect** from the left-side menu:</span></span>

![Screenshot des linksseitigen Menüs der PIX-Anwendung mit hervorgehobener Schaltfläche "verbinden"](images/pix-img-11.png)

2. <span data-ttu-id="f8529-140">Klicken Sie auf der Registerkarte **Computer** auf **Hinzufügen** , und geben Sie folgende Anmelde Informationen ein:</span><span class="sxs-lookup"><span data-stu-id="f8529-140">From the **Computer** tab, click **Add** and enter the following credentials:</span></span>
    * <span data-ttu-id="f8529-141">Alias: der Ermessen des Benutzers</span><span class="sxs-lookup"><span data-stu-id="f8529-141">Alias: Up to user’s discretion</span></span>
    * <span data-ttu-id="f8529-142">Hostname oder IP-Adresse: 127.0.0.1</span><span class="sxs-lookup"><span data-stu-id="f8529-142">Host Name or IP Address: 127.0.0.1</span></span>

3. <span data-ttu-id="f8529-143">Klicken Sie unten rechts auf der Registerkarte **Computer** auf **verbinden** :</span><span class="sxs-lookup"><span data-stu-id="f8529-143">Click **Connect** in the lower-right of the **Computer** tab:</span></span>

![Screenshot des pix-Anwendungs Verbindungs Fensters mit hervorgehobenem Alias, Hostname, IP-Adresse und Schaltfläche "hinzufügen"](images/pix-img-12.png)

> [!NOTE]
> <span data-ttu-id="f8529-145">Die erste Verbindung ist immer langsamer, da Binärdateien kopiert werden.</span><span class="sxs-lookup"><span data-stu-id="f8529-145">The first connection is always slower because binaries are being copied.</span></span>

4. <span data-ttu-id="f8529-146">Wenn pix mit den hololens 2 verbunden ist, suchen Sie Ihre APP im Abschnitt **Ziel Prozess auswählen** auf der Registerkarte "UWP starten", und klicken Sie auf " **starten**":</span><span class="sxs-lookup"><span data-stu-id="f8529-146">When PIX has connected to the HoloLens 2, find your app in the **Select Target Process** section in the Launch UWP tab, and click **Launch**:</span></span>

![Screenshot der PIX-Anwendung mit hervorgehobenem Ziel Prozessfenster auswählen und Start Schaltfläche](images/pix-img-13.png)

## <a name="gpu-captured"></a><span data-ttu-id="f8529-148">GPU aufgezeichnet</span><span class="sxs-lookup"><span data-stu-id="f8529-148">GPU captured</span></span>

1. <span data-ttu-id="f8529-149">Starten Sie die GPU-Erfassung, indem Sie im Abschnitt **GPU-Erfassung** auf **Foto** klicken:</span><span class="sxs-lookup"><span data-stu-id="f8529-149">Start the GPU capture by clicking **Photo** in the **GPU Capture** section:</span></span>

![Screenshot der PIX-Anwendung, bei der der PC-Verbindungsbereich geöffnet ist und GPU-Erfassung hervorgehoben ist](images/pix-img-14.png)

2. <span data-ttu-id="f8529-151">Öffnen Sie die Erfassung für die Analyse, indem Sie im **GPU-Erfassungs** Bereich auf den generierten Screenshot klicken:</span><span class="sxs-lookup"><span data-stu-id="f8529-151">Open the capture for analysis by clicking on the generated screen shot in the **GPU Capture** panel:</span></span>

![Screenshot der PIX-Anwendung mit hervorgehobenem GPU-Erfassungsbereich mit hervorgehobenem GPU-Erfassungsbereich](images/pix-img-15.png)

3. <span data-ttu-id="f8529-153">Klicken Sie auf starten, um die Analyse zu **starten** :</span><span class="sxs-lookup"><span data-stu-id="f8529-153">Press **Start** to begin the analysis:</span></span>

![Screenshot der PIX-Anwendung mit hervorgehobener Schaltfläche "Start"](images/pix-img-16.png)

> [!IMPORTANT]
> <span data-ttu-id="f8529-155">Wenn Sie Zeit Steuerungsdaten sammeln, nachdem Sie eine GPU-Erfassung durch genommen haben, müssen Sie das Headset neu starten.</span><span class="sxs-lookup"><span data-stu-id="f8529-155">If you collect timing data after taking a GPU capture, you'll be required to reboot the headset.</span></span> <span data-ttu-id="f8529-156">Hierbei handelt es sich um einen einmaligen Neustart des Geräts, der für die Erfassung von Zeit Steuerungsdaten erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="f8529-156">This is a one-time restart of the device and is required for timing data collection.</span></span>

<span data-ttu-id="f8529-157">PIX ist jetzt einsatzbereit!</span><span class="sxs-lookup"><span data-stu-id="f8529-157">PIX is now ready for use!</span></span>

## <a name="see-also"></a><span data-ttu-id="f8529-158">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="f8529-158">See also</span></span>
* [<span data-ttu-id="f8529-159">Pix-Homepage</span><span class="sxs-lookup"><span data-stu-id="f8529-159">PIX homepage</span></span>](https://devblogs.microsoft.com/pix)