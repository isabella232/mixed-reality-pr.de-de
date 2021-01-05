---
title: Installieren von PIX für HoloLens 2
description: Erfahren Sie, wie Sie pix für hololens 2-Geräte installieren.
author: hferrone
ms.author: flbagar
ms.date: 12/02/2020
ms.topic: article
keywords: Hololens, hololens 2, pix, Capture, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 598a6b891798be7059eae2eff578c6bbbae442f6
ms.sourcegitcommit: 9d79aaa313f003dd42d5610d458031890776ee8e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/30/2020
ms.locfileid: "97822924"
---
# <a name="installing-pix-for-hololens-2"></a><span data-ttu-id="2979d-104">Installieren von PIX für HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="2979d-104">Installing PIX for HoloLens 2</span></span>

<span data-ttu-id="2979d-105">[Pix](https://devblogs.microsoft.com/pix) ist ein Tool zur Leistungsoptimierung und-Debuggen für DirectX 12-Anwendungen unter Windows.</span><span class="sxs-lookup"><span data-stu-id="2979d-105">[PIX](https://devblogs.microsoft.com/pix) is a performance tuning and debugging tool for DirectX 12 applications on Windows.</span></span> 

## <a name="setup"></a><span data-ttu-id="2979d-106">Einrichten</span><span class="sxs-lookup"><span data-stu-id="2979d-106">Setup</span></span>

1. <span data-ttu-id="2979d-107">Holen Sie sich die neueste pix- [Version]( https://devblogs.microsoft.com/pix/download) von Ihrem Host-PC, und verbinden Sie Ihre hololens 2 über ein USB-Kabel mit Ihrem PC.</span><span class="sxs-lookup"><span data-stu-id="2979d-107">Grab the latest PIX [release]( https://devblogs.microsoft.com/pix/download) from your host PC and connect your HoloLens 2 to your PC via a USB cable.</span></span>

2. <span data-ttu-id="2979d-108">Wenn sich Ihre hololens 2 in einem [Windows Insider-Build](https://insider.windows.com) befinden oder über eine Konfiguration verfügen, die pix unterbricht, löschen  [Sie Ihr Gerät](https://docs.microsoft.com/hololens/hololens-recovery) , um alle Daten zu löschen.</span><span class="sxs-lookup"><span data-stu-id="2979d-108">If your HoloLens 2 is on a [Windows Insider build](https://insider.windows.com) or has a configuration that breaks PIX,  [reflash your device](https://docs.microsoft.com/hololens/hololens-recovery) to erase all data.</span></span>

3. <span data-ttu-id="2979d-109">**Entwicklermodus** und **Geräte Portal** aktivieren:</span><span class="sxs-lookup"><span data-stu-id="2979d-109">Enable **Developer Mode** and **Device Portal**:</span></span>

* <span data-ttu-id="2979d-110">Öffnen Sie die **Einstellungen** von Mixed Reality Home:</span><span class="sxs-lookup"><span data-stu-id="2979d-110">Open **Settings** from Mixed Reality Home:</span></span>

![Screenshot des Menüs "hololens" mit hervorgehobener Einstellungs Schaltfläche](images/pix-img-01.jpg)

* <span data-ttu-id="2979d-112">Wählen Sie **Update & Sicherheit**:</span><span class="sxs-lookup"><span data-stu-id="2979d-112">Select **Update & Security**:</span></span>

![Screenshot des Fensters "Einstellungen" in hololens mit hervorgehobener Schaltfläche "aktualisieren und Sicherheit"](images/pix-img-02.jpg)

* <span data-ttu-id="2979d-114">Wählen Sie **für Entwickler**:</span><span class="sxs-lookup"><span data-stu-id="2979d-114">Select **For Developers**:</span></span>

![Screenshot der Schaltfläche "Sicherheit und Updates" mit hervorgehobener Schaltfläche "Entwickler"](images/pix-img-03.jpg)

* <span data-ttu-id="2979d-116">Aktivieren der **Verwendung von Entwickler Features** und **Aktivieren des Geräte Portals**</span><span class="sxs-lookup"><span data-stu-id="2979d-116">Turn on **Use Developer Features** and **Enable Device Portal**</span></span>

![Screenshot des Fensters "Entwickler" in den Einstellungen "Geräte Portal aktivieren"](images/pix-img-04.jpg)

![Screenshot des Fensters "Entwickler" in "Einstellungen" mit der Schaltfläche "entwickeln von Features umschalten"](images/pix-img-05.jpg)

* <span data-ttu-id="2979d-119">Starten Sie Visual Studio, wenn das Gerät immer noch verbunden ist, aktiv ist und der Benutzer angemeldet ist.</span><span class="sxs-lookup"><span data-stu-id="2979d-119">With the device still connected, awake, and with the user logged in, launch Visual Studio.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2979d-120">Stellen Sie sicher, dass sich Ihr Gerät nicht im Standbymodus befindet oder nicht</span><span class="sxs-lookup"><span data-stu-id="2979d-120">Make sure your device isn't in standby mode or asleep.</span></span> <span data-ttu-id="2979d-121">Wenn Sie Probleme mit diesem Schritt haben, finden Sie die [Anweisungen im Windows-Geräte Portal](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal).</span><span class="sxs-lookup"><span data-stu-id="2979d-121">If you're having trouble with this step, refer to the [Windows Device Portal instructions](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal).</span></span>

## <a name="preparing-for-deployment"></a><span data-ttu-id="2979d-122">Vorbereiten der Bereitstellung</span><span class="sxs-lookup"><span data-stu-id="2979d-122">Preparing for deployment</span></span>

1. <span data-ttu-id="2979d-123">Legen Sie in Visual Studio **ARM64** als Plattform und **Gerät** als Gerät fest:</span><span class="sxs-lookup"><span data-stu-id="2979d-123">In Visual Studio, set **ARM64** as the platform and **Device** as the device:</span></span>

![Screenshot der Visual Studio-Projekt Mappe mit hervorgehobenen Plattform-und Geräteeinstellungen](images/pix-img-06.png)

2. <span data-ttu-id="2979d-125">Wenn Sie von Visual Studio aufgefordert werden, eine **Pin** vom Gerät einzugeben:</span><span class="sxs-lookup"><span data-stu-id="2979d-125">When Visual Studio prompts you for a **PIN** from the device:</span></span>

![Screenshot der Visual Studio-Popup-Aufforderung zur PIN](images/pix-img-07.png)

* <span data-ttu-id="2979d-127">Auswählen von **Einstellungen** aus der Shell</span><span class="sxs-lookup"><span data-stu-id="2979d-127">Select **Settings** from Shell</span></span>
* <span data-ttu-id="2979d-128">Wählen Sie **Update & Sicherheit** aus.</span><span class="sxs-lookup"><span data-stu-id="2979d-128">Select **Update & Security**</span></span>
* <span data-ttu-id="2979d-129">Wählen Sie **für Entwickler aus** , und klicken Sie unter **Geräte** Ermittlung auf paar</span><span class="sxs-lookup"><span data-stu-id="2979d-129">Select **For Developers** and press Pair under **Device Discovery**</span></span> 

![Screenshot von für Entwickler Fenster "in Einstellungen öffnen" mit hervorgehobener Geräte Ermittlung](images/pix-img-08.jpg)

![Screenshot des Popups für kostenpflichtige Geräte mit hervorgehobenem Registrierungscode](images/pix-img-09.jpg)

* <span data-ttu-id="2979d-132">Geben Sie die generierte PIN-Nummer in Visual Studio ein.</span><span class="sxs-lookup"><span data-stu-id="2979d-132">Enter the generated PIN number in Visual Studio</span></span>

3. <span data-ttu-id="2979d-133">Visual Studio stellt die app in den verbundenen hololens 2 bereit. Dies kann je nach App einige Minuten dauern.</span><span class="sxs-lookup"><span data-stu-id="2979d-133">Visual Studio will deploy the app to the connected HoloLens 2, which may take a few minutes depending on the app.</span></span>

## <a name="launching-pix"></a><span data-ttu-id="2979d-134">Starten von Pix</span><span class="sxs-lookup"><span data-stu-id="2979d-134">Launching PIX</span></span>

<span data-ttu-id="2979d-135">Überprüfen Sie zunächst mithilfe des Geräte Portals, ob die APP auf den hololens 2 ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="2979d-135">First, use Device Portal to verify the app isn't running on the HoloLens 2.</span></span> <span data-ttu-id="2979d-136">Starten Sie dann pix, stellen Sie eine Verbindung mit Ihrem Gerät her, und wählen Sie **Startseite**:</span><span class="sxs-lookup"><span data-stu-id="2979d-136">Then, launch PIX, connect to your device, and select **Home**:</span></span>

![Screenshot des pix-Anwendungs-Startbildschirms](images/pix-img-10.png)

* <span data-ttu-id="2979d-138">Wählen Sie im Menü auf der linken Seite die Option **verbinden** aus:</span><span class="sxs-lookup"><span data-stu-id="2979d-138">Select **Connect** from the left-side menu:</span></span>

![Screenshot des linksseitigen Menüs der PIX-Anwendung mit hervorgehobener Schaltfläche "verbinden"](images/pix-img-11.png)

2. <span data-ttu-id="2979d-140">Klicken Sie auf der Registerkarte **Computer** auf **Hinzufügen**, und geben Sie die folgenden Anmelde Informationen ein:</span><span class="sxs-lookup"><span data-stu-id="2979d-140">From the **Computer** tab, select **Add**, and enter the following credentials:</span></span>
    * <span data-ttu-id="2979d-141">Alias: der Ermessen des Benutzers</span><span class="sxs-lookup"><span data-stu-id="2979d-141">Alias: Up to user’s discretion</span></span>
    * <span data-ttu-id="2979d-142">Hostname oder IP-Adresse: 127.0.0.1</span><span class="sxs-lookup"><span data-stu-id="2979d-142">Host Name or IP Address: 127.0.0.1</span></span>

3. <span data-ttu-id="2979d-143">Wählen Sie in der unteren rechten Ecke der Registerkarte **Computer** die Option **verbinden** aus:</span><span class="sxs-lookup"><span data-stu-id="2979d-143">Select **Connect** in the lower right of the **Computer** tab:</span></span>

![Screenshot des pix-Anwendungs Verbindungs Fensters mit hervorgehobenem Alias, Hostname, IP-Adresse und Schaltfläche "hinzufügen"](images/pix-img-12.png)

> [!NOTE]
> <span data-ttu-id="2979d-145">Die erste Verbindung ist immer langsamer, da Binärdateien kopiert werden.</span><span class="sxs-lookup"><span data-stu-id="2979d-145">The first connection is always slower because binaries are being copied.</span></span>

4. <span data-ttu-id="2979d-146">Wenn pix mit den hololens 2 verbunden ist, suchen Sie Ihre APP im Abschnitt **Ziel Prozess auswählen** auf der Registerkarte "UWP starten", und wählen Sie " **starten**" aus:</span><span class="sxs-lookup"><span data-stu-id="2979d-146">When PIX has connected to the HoloLens 2, find your app in the **Select Target Process** section in the Launch UWP tab, and select **Launch**:</span></span>

![Screenshot der PIX-Anwendung mit hervorgehobenem Ziel Prozessfenster auswählen und Start Schaltfläche](images/pix-img-13.png)

## <a name="gpu-captured"></a><span data-ttu-id="2979d-148">GPU aufgezeichnet</span><span class="sxs-lookup"><span data-stu-id="2979d-148">GPU captured</span></span>

1. <span data-ttu-id="2979d-149">Starten Sie die GPU-Erfassung, indem Sie im Abschnitt **GPU-Erfassung** auf **Foto** klicken:</span><span class="sxs-lookup"><span data-stu-id="2979d-149">Start the GPU capture by clicking **Photo** in the **GPU Capture** section:</span></span>

![Screenshot der PIX-Anwendung, bei der der PC-Verbindungsbereich geöffnet ist und GPU-Erfassung hervorgehoben ist](images/pix-img-14.png)

2. <span data-ttu-id="2979d-151">Öffnen Sie die Erfassung für die Analyse, indem Sie im GPU- **Erfassungs** Bereich auf den generierten Screenshot klicken:</span><span class="sxs-lookup"><span data-stu-id="2979d-151">Open the capture for analysis by clicking on the generated screenshot in the **GPU Capture** panel:</span></span>

![Screenshot der PIX-Anwendung mit hervorgehobenem GPU-Erfassungsbereich mit hervorgehobenem GPU-Erfassungsbereich](images/pix-img-15.png)

3. <span data-ttu-id="2979d-153">Klicken Sie auf starten, um die Analyse zu **starten** :</span><span class="sxs-lookup"><span data-stu-id="2979d-153">Press **Start** to begin the analysis:</span></span>

![Screenshot der PIX-Anwendung mit hervorgehobener Schaltfläche "Start"](images/pix-img-16.png)

> [!IMPORTANT]
> <span data-ttu-id="2979d-155">Wenn Sie Zeit Steuerungsdaten sammeln, nachdem Sie eine GPU-Erfassung durch genommen haben, müssen Sie das Headset neu starten.</span><span class="sxs-lookup"><span data-stu-id="2979d-155">If you collect timing data after taking a GPU capture, you'll be required to reboot the headset.</span></span> <span data-ttu-id="2979d-156">Hierbei handelt es sich um einen einmaligen Neustart des Geräts, der für die Erfassung von Zeit Steuerungsdaten erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="2979d-156">This is a one-time restart of the device and is required for timing data collection.</span></span>

<span data-ttu-id="2979d-157">PIX ist jetzt einsatzbereit!</span><span class="sxs-lookup"><span data-stu-id="2979d-157">PIX is now ready for use!</span></span>

## <a name="see-also"></a><span data-ttu-id="2979d-158">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="2979d-158">See also</span></span>
* [<span data-ttu-id="2979d-159">Pix-Homepage</span><span class="sxs-lookup"><span data-stu-id="2979d-159">PIX homepage</span></span>](https://devblogs.microsoft.com/pix)