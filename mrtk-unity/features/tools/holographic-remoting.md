---
title: Holographic Remoting
description: 'Dokumentation: Holographic Remoting MRTK'
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 637f68e5ad5f360aea4b5c0603a682d61d152a89
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144582"
---
# <a name="holographic-remoting"></a><span data-ttu-id="851f1-104">Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="851f1-104">Holographic Remoting</span></span>

<span data-ttu-id="851f1-105">Holographic Remoting streamt holografische Inhalte in Echtzeit über eine Wi-Fi- oder USB-Kabelverbindung von einem PC an Ihren Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="851f1-105">Holographic remoting streams holographic content from a PC to your Microsoft HoloLens in real-time, using a Wi-Fi or USB cable connection.</span></span> <span data-ttu-id="851f1-106">Dieses Feature kann die Produktivität von Entwicklern bei der Entwicklung von Mixed Reality-Anwendungen erheblich steigern.</span><span class="sxs-lookup"><span data-stu-id="851f1-106">This feature can significantly increase developer productivity when developing mixed reality applications.</span></span>

<span data-ttu-id="851f1-107">Das XR SDK bezieht sich wie unten erwähnt auf die [neue XR-Pipeline von Unity in Unity 2019.3 und darüber hinaus.](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/)</span><span class="sxs-lookup"><span data-stu-id="851f1-107">XR SDK as mentioned below refers to Unity's [new XR pipeline in Unity 2019.3 and beyond](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span></span> <span data-ttu-id="851f1-108">Weitere Informationen zur Verwendung des XR SDK mit MRTK finden Sie [hier.](../../configuration/getting-started-with-mrtk-and-xrsdk.md)</span><span class="sxs-lookup"><span data-stu-id="851f1-108">See [here](../../configuration/getting-started-with-mrtk-and-xrsdk.md) for more information on using XR SDK with MRTK.</span></span> <span data-ttu-id="851f1-109">Legacy-XR bezieht sich auf die vorhandene XR-Pipeline, die in Unity 2018 enthalten ist, in Unity 2019.3 veraltet ist und in Unity 2020 entfernt wurde.</span><span class="sxs-lookup"><span data-stu-id="851f1-109">Legacy XR refers to the existing XR pipeline that is included in Unity 2018, deprecated in Unity 2019.3 and removed in Unity 2020.</span></span>

## <a name="initial-setup"></a><span data-ttu-id="851f1-110">Erste Einrichtung</span><span class="sxs-lookup"><span data-stu-id="851f1-110">Initial setup</span></span>

<span data-ttu-id="851f1-111">Um Remoting für eine HoloLens zu aktivieren, müssen Sie sicherstellen, dass das Projekt die neuesten Remotingkomponenten verwendet.</span><span class="sxs-lookup"><span data-stu-id="851f1-111">To enable remoting to a HoloLens, it is important to ensure that the project is using the latest remoting components.</span></span>

1. <span data-ttu-id="851f1-112">> Paket-Manager **"Fenster öffnen"**</span><span class="sxs-lookup"><span data-stu-id="851f1-112">Open **Window > Package Manager**</span></span>
    - <span data-ttu-id="851f1-113">Bei Verwendung von Legacy-XR: Überprüfen Sie, ob die neueste Version des **Windows Mixed Reality** Pakets installiert ist.</span><span class="sxs-lookup"><span data-stu-id="851f1-113">If using legacy XR: Verify that latest version of the **Windows Mixed Reality** package is installed.</span></span>
    - <span data-ttu-id="851f1-114">Bei Verwendung des XR SDK: Überprüfen Sie, ob die neueste Version des **Windows XR-Plug-In-Pakets** installiert ist.</span><span class="sxs-lookup"><span data-stu-id="851f1-114">If using XR SDK: Verify that latest version of the **Windows XR Plugin** package is installed.</span></span>
1. <span data-ttu-id="851f1-115">Stellen Sie sicher, dass die neueste Holographic Remoting-Anwendung auf der HoloLens über die Microsoft Store installiert ist.</span><span class="sxs-lookup"><span data-stu-id="851f1-115">Ensure the latest Holographic Remoting application is installed, on the HoloLens, via the Microsoft Store.</span></span>

<span data-ttu-id="851f1-116">Fahren Sie mit [Legacy-XR-Setupanweisungen](#legacy-xr-setup-instructions) oder [XR SDK-Setupanweisungen](#xr-sdk-setup-instructions) fort, je nachdem, welche Pipeline im Projekt verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="851f1-116">Please continue to [Legacy XR setup instructions](#legacy-xr-setup-instructions) or [XR SDK setup instructions](#xr-sdk-setup-instructions) depending on which pipeline is used in the project.</span></span>

## <a name="legacy-xr-setup-instructions"></a><span data-ttu-id="851f1-117">Legacy-XR-Setupanweisungen</span><span class="sxs-lookup"><span data-stu-id="851f1-117">Legacy XR setup instructions</span></span>

<span data-ttu-id="851f1-118">Die folgenden Anweisungen gelten nur für Remoting mit HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="851f1-118">The instructions below only apply to remoting with HoloLens 2.</span></span> <span data-ttu-id="851f1-119">Wenn Sie nur Remoting mit HoloLens (1. Generation) ausführen, fahren Sie mit [Herstellen einer Verbindung mit HoloLens mit WLAN](#connecting-to-the-hololens-with-wi-fi)weiter.</span><span class="sxs-lookup"><span data-stu-id="851f1-119">If you only perform remoting with HoloLens (1st Gen), skip to [Connecting to the HoloLens with Wi-Fi](#connecting-to-the-hololens-with-wi-fi).</span></span>

<span data-ttu-id="851f1-120">Bei Verwendung eines HoloLens 2 wurde MRTK Unterstützung für Remoting von Hand- und Blickverfolgungsdaten hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="851f1-120">When using a HoloLens 2, support for remoting articulated hand and eye tracking data has been added to MRTK.</span></span> <span data-ttu-id="851f1-121">Um diese Funktionen zu aktivieren, führen Sie die Schritte aus, die unter [Importieren von DotNetWinRT in das Projekt](#import-dotnetwinrt-into-the-project)dokumentiert sind.</span><span class="sxs-lookup"><span data-stu-id="851f1-121">To enable these features, please follow the steps documented in [Import DotNetWinRT into the project](#import-dotnetwinrt-into-the-project).</span></span>

<span data-ttu-id="851f1-122">Nach dem Importieren besteht der nächste Schritt darin, **Mixed Reality**  >  **Toolkit-Hilfsprogramme**  >  **Windows Mixed Reality**  >  **Konfiguration überprüfen** auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="851f1-122">Once imported, the next step is to select **Mixed Reality Toolkit** > **Utilities** > **Windows Mixed Reality** > **Check Configuration**.</span></span> <span data-ttu-id="851f1-123">In diesem Schritt wird eine Skripterstellungs-Definition hinzugefügt, die die DotNetWinRT-Abhängigkeit aktiviert.</span><span class="sxs-lookup"><span data-stu-id="851f1-123">This step adds a scripting define that enables the DotNetWinRT dependency.</span></span>

> [!NOTE]
> <span data-ttu-id="851f1-124">Bei Verwendung von Unity 2019.4 und neuer ist es nicht erforderlich, das Hilfsprogramm Konfiguration überprüfen auszuführen.</span><span class="sxs-lookup"><span data-stu-id="851f1-124">When using Unity 2019.4 and newer, it is not necessary to run the Check Configuration utility.</span></span>

<span data-ttu-id="851f1-125">Führen Sie die Schritte in den Abschnitten Debuggen HoloLens 2 **Remoting** per Unity-Paketimport und verwandten Abschnitten aus, um die Nachverfolgung von Handgelenken und Eyetracking zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="851f1-125">To enable tracking of hand joints and eye tracking, follow the steps in the **Debugging HoloLens 2 remoting via Unity package import** and related sections.</span></span>

### <a name="debugging-hololens-2-remoting-via-unity-package-import"></a><span data-ttu-id="851f1-126">Debuggen HoloLens 2 remoting per Unity-Paketimport</span><span class="sxs-lookup"><span data-stu-id="851f1-126">Debugging HoloLens 2 remoting via Unity package import</span></span>

<span data-ttu-id="851f1-127">Wenn HoloLens 2 Hand- und Eyetracking nicht über Remoting arbeiten, gibt es einige häufige Probleme.</span><span class="sxs-lookup"><span data-stu-id="851f1-127">If HoloLens 2 hand joints and eye tracking aren't working over remoting, there are a few common points of potential issues.</span></span> <span data-ttu-id="851f1-128">Sie sind unten in der Reihenfolge aufgeführt, in der sie überprüft werden sollten.</span><span class="sxs-lookup"><span data-stu-id="851f1-128">They're listed below in the order they should be checked.</span></span>

<span data-ttu-id="851f1-129">Diese Probleme sind besonders relevant, wenn sie unter **Unity 2019.3 oder** höher ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="851f1-129">These issues are particularly relevant when running on **Unity 2019.3** or later.</span></span>

#### <a name="import-dotnetwinrt-into-the-project"></a><span data-ttu-id="851f1-130">Importieren von DotNetWinRT in das Projekt</span><span class="sxs-lookup"><span data-stu-id="851f1-130">Import DotNetWinRT into the project</span></span>

1. <span data-ttu-id="851f1-131">Herunterladen des [Mixed Reality Featuretools](https://aka.ms/MRFeatureTool)</span><span class="sxs-lookup"><span data-stu-id="851f1-131">Download the [Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool)</span></span>

1. <span data-ttu-id="851f1-132">Wählen Sie **in der Ansicht** Features entdecken Mixed Reality *WinRT-Projektionen aus.*</span><span class="sxs-lookup"><span data-stu-id="851f1-132">In the **Discover features** view, select *Mixed Reality WinRT Projections*</span></span>

    ![Auswählen des DotNetWinRT-Pakets](../images/tools/remoting/SelectDotNetWinRT.png)

1. <span data-ttu-id="851f1-134">Klicken **Sie auf Features erhalten,** und fahren Sie mit dem Importieren des [Pakets fort.](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool#3-importing-feature-packages)</span><span class="sxs-lookup"><span data-stu-id="851f1-134">Click **Get Features** and continue to [import the package](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool#3-importing-feature-packages).</span></span>

#### <a name="dotnetwinrt_present-define-written-into-player-settings"></a><span data-ttu-id="851f1-135">DOTNETWINRT_PRESENT definition written into player settings (In Playereinstellungen geschriebene Definition)</span><span class="sxs-lookup"><span data-stu-id="851f1-135">DOTNETWINRT_PRESENT define written into player settings</span></span>

> [!NOTE]
> <span data-ttu-id="851f1-136">Bei Verwendung von Unity 2019.4 und neuer ist die DOTNETWINRT_PRESENT-Definition in den entsprechenden ASMDEF-Dateien und nicht in den Unity Player-Einstellungen enthalten.</span><span class="sxs-lookup"><span data-stu-id="851f1-136">When using Unity 2019.4 and newer, the DOTNETWINRT_PRESENT define is contained within the appropriate .asmdef files and not the Unity Player Settings.</span></span> <span data-ttu-id="851f1-137">Der Schritt Konfiguration überprüfen ist nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="851f1-137">The Check Configuration step is not required.</span></span>

<span data-ttu-id="851f1-138">Ab MRTK Version 2.5.0 wird diese #define aus Leistungsgründen nicht mehr automatisch festgelegt.</span><span class="sxs-lookup"><span data-stu-id="851f1-138">Beginning with MRTK version 2.5.0, for performance reasons, this #define is no longer automatically set.</span></span> <span data-ttu-id="851f1-139">Um dieses Flag zu aktivieren, verwenden Sie Mixed Reality Toolkit-Hilfsprogramme  >    >  **Windows Mixed Reality**  >  **Menüelement Konfiguration** überprüfen.</span><span class="sxs-lookup"><span data-stu-id="851f1-139">To enable this flag, please use the **Mixed Reality Toolkit** > **Utilities** > **Windows Mixed Reality** > **Check Configuration** menu item.</span></span>

> [!Note]
> <span data-ttu-id="851f1-140">Das Element Konfiguration überprüfen zeigt keine Bestätigung an.</span><span class="sxs-lookup"><span data-stu-id="851f1-140">The Check Configuration item does not display a confirmation.</span></span> <span data-ttu-id="851f1-141">Um zu bestätigen, dass die Definition festgelegt wurde, navigieren Sie zu unity player settings (Unity-Playereinstellungen).</span><span class="sxs-lookup"><span data-stu-id="851f1-141">To confirm that the define has been set, please navigate to the Unity Player Settings.</span></span> <span data-ttu-id="851f1-142">Überprüfen Sie dort auf der Registerkarte UWP unter Weitere Einstellungen die Skripterstellung Symbole definieren.</span><span class="sxs-lookup"><span data-stu-id="851f1-142">From there, under the UWP tab, check under Other Settings for the Scripting Define Symbols.</span></span> <span data-ttu-id="851f1-143">Stellen Sie sicher, DOTNETWINRT_PRESENT ordnungsgemäß in diese Liste geschrieben ist.</span><span class="sxs-lookup"><span data-stu-id="851f1-143">Make sure DOTNETWINRT_PRESENT is properly written in that list.</span></span> <span data-ttu-id="851f1-144">Wenn dies der Fall ist, war dieser Schritt erfolgreich.</span><span class="sxs-lookup"><span data-stu-id="851f1-144">If that's there, this step succeeded.</span></span>

![DotNetWinRT Present](../images/tools/remoting/DotNetWinRTPresent.png)

### <a name="removing-hololens-2-specific-remoting-support"></a><span data-ttu-id="851f1-146">Entfernen HoloLens 2-spezifischer Remotingunterstützung</span><span class="sxs-lookup"><span data-stu-id="851f1-146">Removing HoloLens 2-specific remoting support</span></span>

<span data-ttu-id="851f1-147">Wenn aufgrund des Vorhandenseins des DotNetWinRT-Adapters Konflikte oder andere Probleme auftreten, wenden Sie [sich an eine unserer Hilferessourcen.](../../index.md#getting-help)</span><span class="sxs-lookup"><span data-stu-id="851f1-147">If you're running into conflicts or other issues due to the presence of the DotNetWinRT adapter, please [reach out on one of our help resources](../../index.md#getting-help).</span></span>

## <a name="xr-sdk-setup-instructions"></a><span data-ttu-id="851f1-148">Setupanweisungen für das XR SDK</span><span class="sxs-lookup"><span data-stu-id="851f1-148">XR SDK setup instructions</span></span>

<span data-ttu-id="851f1-149">Befolgen Sie die [Windows Mixed Reality Setupanweisungen auf der Seite Erste Schritte mit MRTK und XR SDK,](../../configuration/getting-started-with-mrtk-and-xrsdk.md#windows-mixed-reality) und stellen Sie sicher, dass Sie den für HoloLens-Remoting im Editor erforderlichen Schritt ausführen.</span><span class="sxs-lookup"><span data-stu-id="851f1-149">Follow the [Windows Mixed Reality setup instructions on the Getting started with MRTK and XR SDK page](../../configuration/getting-started-with-mrtk-and-xrsdk.md#windows-mixed-reality) and make sure to perform the step required for in-editor HoloLens Remoting.</span></span>

## <a name="connecting-to-the-hololens-with-wi-fi"></a><span data-ttu-id="851f1-150">Herstellen einer Verbindung mit HoloLens mit Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="851f1-150">Connecting to the HoloLens with Wi-Fi</span></span>

<span data-ttu-id="851f1-151">Nachdem das Projekt konfiguriert wurde, kann eine Verbindung mit der HoloLens hergestellt werden.</span><span class="sxs-lookup"><span data-stu-id="851f1-151">Once the project has been configured, a connection can be established to the HoloLens.</span></span>

1. <span data-ttu-id="851f1-152">Stellen Sie **unter Datei > Buildeinstellungen** sicher, dass der Projektbuildtyp auf **Universelle Windows-Plattform**</span><span class="sxs-lookup"><span data-stu-id="851f1-152">In **File > Build Settings**, ensure that the project build type is set to **Universal Windows Platform**</span></span>
1. <span data-ttu-id="851f1-153">Starten Sie auf der HoloLens die **Holographic Remoting-Anwendung.**</span><span class="sxs-lookup"><span data-stu-id="851f1-153">On the HoloLens, launch the **Holographic Remoting** application.</span></span>
1. <span data-ttu-id="851f1-154">Wählen Sie in Unity **Window > XR > Holographic Emulation (bei Verwendung von Legacy-XR) /Windows XR-Plug-In-Remoting (bei Verwendung des XR SDK) aus.**</span><span class="sxs-lookup"><span data-stu-id="851f1-154">In Unity, select **Window > XR > Holographic Emulation (if using legacy XR) / Windows XR Plugin Remoting (if using XR SDK)**.</span></span>

    ![Starten der Holographic Emulation](../images/tools/remoting/StartHolographicEmulation.png)

1. <span data-ttu-id="851f1-156">Legen Sie **emulation mode (Emulationsmodus)** auf **Remote auf Device (Gerät) fest.**</span><span class="sxs-lookup"><span data-stu-id="851f1-156">Set **Emulation Mode** to **Remote to Device**.</span></span>

    ![Festlegen des Emulationsmodus](../images/tools/remoting/SelectEmulationMode.png)

1. <span data-ttu-id="851f1-158">(**_Gilt nur für legacy XR_**) Wählen Sie die **Geräteversion aus.**</span><span class="sxs-lookup"><span data-stu-id="851f1-158">(**_Only applies to legacy XR_**) Select the **Device Version**.</span></span>

    ![Auswählen der Geräteversion](../images/tools/remoting/SelectDeviceVersion.png)

1. <span data-ttu-id="851f1-160">Legen Sie mithilfe der IP-Adresse, die von der Holographic Remoting Player-Anwendung angezeigt wird, das Feld **Remotecomputer** fest.</span><span class="sxs-lookup"><span data-stu-id="851f1-160">Using the IP Address displayed by the Holographic Remoting Player application, set the **Remote Machine** field.</span></span>

    ![Geben Sie die IP-Adresse ein.](../images/tools/remoting/EnterIPAddress.png)

1. <span data-ttu-id="851f1-162">Klicken Sie auf **Verbinden**.</span><span class="sxs-lookup"><span data-stu-id="851f1-162">Click **Connect**.</span></span>

> [!NOTE]
> <span data-ttu-id="851f1-163">Wenn Sie keine Verbindung herstellen können, stellen Sie sicher, dass Ihr HoloLens 2 nicht an Ihren PC angeschlossen ist, und starten Sie Unity neu.</span><span class="sxs-lookup"><span data-stu-id="851f1-163">If you cannot connect, make sure your HoloLens 2 is not plugged in to your PC and restart Unity.</span></span>

## <a name="connecting-to-the-hololens-with-usb-cable"></a><span data-ttu-id="851f1-164">Herstellen einer Verbindung mit der HoloLens per USB-Kabel</span><span class="sxs-lookup"><span data-stu-id="851f1-164">Connecting to the HoloLens with USB cable</span></span>

<span data-ttu-id="851f1-165">Usb-Kabelverbindung bietet eine bessere Renderingqualität und Stabilität.</span><span class="sxs-lookup"><span data-stu-id="851f1-165">USB cable connection gives better rendering quality and stability.</span></span> <span data-ttu-id="851f1-166">Um die USB-Kabelverbindung zu verwenden, trennen Sie die HoloLens Wi-Fi in den HoloLens-Einstellungen, und starten Sie die Holographic Remoting Player-App.</span><span class="sxs-lookup"><span data-stu-id="851f1-166">To use USB cable connection, disconnect from the HoloLens from Wi-Fi in HoloLens's Settings and launch Holographic Remoting Player app.</span></span> <span data-ttu-id="851f1-167">Es wird eine IP-Adresse angezeigt, die mit 169 beginnt.</span><span class="sxs-lookup"><span data-stu-id="851f1-167">It will display an IP address that starts with 169.</span></span> <span data-ttu-id="851f1-168">Verwenden Sie diese IP-Adresse in der Holographic Emulation-Einstellung von Unity, um eine Verbindung herzustellen.</span><span class="sxs-lookup"><span data-stu-id="851f1-168">Use this IP address in Unity's Holographic Emulation setting to connect.</span></span> <span data-ttu-id="851f1-169">Nachdem die IP-Adresse für das USB-Kabel identifiziert wurde, ist es sicher, die HoloLens wieder mit Wi-Fi verbinden.</span><span class="sxs-lookup"><span data-stu-id="851f1-169">Once the IP address for USB cable has been identified, it is safe to connect the HoloLens to Wi-Fi again.</span></span>

## <a name="starting-a-remoting-session"></a><span data-ttu-id="851f1-170">Starten einer Remotingsitzung</span><span class="sxs-lookup"><span data-stu-id="851f1-170">Starting a remoting session</span></span>

<span data-ttu-id="851f1-171">Wenn Unity mit der HoloLens verbunden ist, wechseln Sie im Editor in den Wiedergabemodus.</span><span class="sxs-lookup"><span data-stu-id="851f1-171">With Unity connected to the HoloLens, enter play mode in the editor.</span></span>

<span data-ttu-id="851f1-172">Wenn die Sitzung abgeschlossen ist, beenden Sie den Wiedergabemodus.</span><span class="sxs-lookup"><span data-stu-id="851f1-172">When the session is complete, exit play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="851f1-173">Es gibt ein bekanntes Problem mit einigen Versionen von Unity, bei dem der Editor während einer Remotingsitzung beim Wechseln in den Wiedergabemodus hängen bleibt.</span><span class="sxs-lookup"><span data-stu-id="851f1-173">There is a known issue with some versions of Unity where the editor may hang upon entering play mode during a remoting session.</span></span> <span data-ttu-id="851f1-174">Dieses Problem kann sich manifestieren, wenn das Holographic-Fenster geöffnet ist, wenn das Projekt geladen wird.</span><span class="sxs-lookup"><span data-stu-id="851f1-174">This issue may manifest if the Holographic window is open when the project is loaded.</span></span> <span data-ttu-id="851f1-175">Um sicherzustellen, dass dieses Problem nicht auftritt, schließen Sie immer den Holographic-Dialog, bevor Sie Unity beenden.</span><span class="sxs-lookup"><span data-stu-id="851f1-175">To ensure this issue does not occur, always close the Holographic dialog prior to exiting Unity.</span></span>

## <a name="see-also"></a><span data-ttu-id="851f1-176">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="851f1-176">See also</span></span>

- [<span data-ttu-id="851f1-177">Problembehandlung und Einschränkungen bei Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="851f1-177">Holographic Remoting troubleshooting and limitations</span></span>](/windows/mixed-reality/holographic-remoting-troubleshooting)
- [<span data-ttu-id="851f1-178">Microsoft Holographic Remoting-Softwarelizenzbedingungen</span><span class="sxs-lookup"><span data-stu-id="851f1-178">Microsoft Holographic Remoting software license terms</span></span>](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)