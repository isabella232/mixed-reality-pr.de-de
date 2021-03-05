---
title: Von openxr-Plug-in unterstützte Funktionen in Unity
description: Entdecken Sie die Features, die openxr für die Entwicklung gemischter Realität in Unity unterstützt.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, Mixed Reality, mrtk, Mixed Reality Toolkit, Augmented Reality, Virtual Reality, Mixed Reality-Headsets, erlernen, Tutorial, Getting Started
ms.openlocfilehash: 0501abe5a417c17283347455ccea8ec6f49a6a45
ms.sourcegitcommit: 4647712788a91a2b26d4b01e62285c2942bb0bd2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102230741"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a><span data-ttu-id="8c72f-104">Gemischte Funktionen von openxr unterstützten Funktionen in Unity</span><span class="sxs-lookup"><span data-stu-id="8c72f-104">Mixed Reality OpenXR supported features in Unity</span></span>

<span data-ttu-id="8c72f-105">Das **gemischte openxr-Plug** -in für die Realität ist eine Erweiterung des Unity **openxr-Plug** -ins und unterstützt eine Reihe von Features für hololens 2-und Windows Mixed Reality-Headsets.</span><span class="sxs-lookup"><span data-stu-id="8c72f-105">The **Mixed Reality OpenXR Plugin** package is an extension of Unity's **OpenXR Plugin** and supports a suite of features for HoloLens 2 and Windows Mixed Reality headsets.</span></span> <span data-ttu-id="8c72f-106">Bevor Sie fortfahren, stellen Sie sicher, dass Sie **Unity 2020,2** oder höher, **openxr Plugin, Version 0.1.3** oder höher, installiert haben und Ihr Unity-Projekt [für openxr konfiguriert](openxr-getting-started.md)ist.</span><span class="sxs-lookup"><span data-stu-id="8c72f-106">Before continuing, make sure that you've installed **Unity 2020.2** or later, **OpenXR Plugin version 0.1.3** or later, and your Unity project is [configured for OpenXR](openxr-getting-started.md).</span></span>

## <a name="whats-supported"></a><span data-ttu-id="8c72f-107">Unterstützte Funktionen</span><span class="sxs-lookup"><span data-stu-id="8c72f-107">What's supported</span></span>

<span data-ttu-id="8c72f-108">Die folgenden Funktionen werden derzeit unterstützt:</span><span class="sxs-lookup"><span data-stu-id="8c72f-108">The following features are currently supported:</span></span>

* <span data-ttu-id="8c72f-109">Unterstützt UWP-Anwendungen für hololens 2 und optimiert für das hololens 2-Anwendungsmodell.</span><span class="sxs-lookup"><span data-stu-id="8c72f-109">Supports UWP applications for HoloLens 2, and optimize for HoloLens 2 application model.</span></span>
* <span data-ttu-id="8c72f-110">Unterstützt Win32-VR-Anwendungen für Windows Mixed Reality-Headset mit den neuesten Controller Profilen und Holographic App-Remoting.</span><span class="sxs-lookup"><span data-stu-id="8c72f-110">Supports Win32 VR applications for Windows Mixed Reality headset with latest controller profiles and holographic app remoting.</span></span>
* <span data-ttu-id="8c72f-111">Welt weite Nachverfolgung mithilfe von Ankern und unbeschränktes Raum.</span><span class="sxs-lookup"><span data-stu-id="8c72f-111">World scale tracking using Anchors and Unbounded space.</span></span>
* <span data-ttu-id="8c72f-112">[Anker-Speicher-API zum Beibehalten von Ankern](#anchors-and-anchor-persistence) an hololens 2 lokalen Speicher.</span><span class="sxs-lookup"><span data-stu-id="8c72f-112">[Anchor storage API to persist anchors](#anchors-and-anchor-persistence) to HoloLens 2 local storage.</span></span>
* <span data-ttu-id="8c72f-113">[Motion Controller und Hand Interaktionen](#motion-controller-and-hand-interactions), einschließlich des neuen HP-Reverb-G2-Controllers.</span><span class="sxs-lookup"><span data-stu-id="8c72f-113">[Motion controller and hand interactions](#motion-controller-and-hand-interactions), including the new HP Reverb G2 controller.</span></span>
* <span data-ttu-id="8c72f-114">Handgelenk Verfolgung mithilfe von 26 Gelenken und gemeinsamen RADIUS-Eingaben.</span><span class="sxs-lookup"><span data-stu-id="8c72f-114">Articulated hand tracking using 26 joints and joint radius inputs.</span></span>
* <span data-ttu-id="8c72f-115">Interaktion mit Blick auf hololens 2.</span><span class="sxs-lookup"><span data-stu-id="8c72f-115">Eye gaze interaction on HoloLens 2.</span></span>
* <span data-ttu-id="8c72f-116">Auffinden von Foto/Video-Kamera (PV) auf hololens 2.</span><span class="sxs-lookup"><span data-stu-id="8c72f-116">Locating photo/video (PV) camera on HoloLens 2.</span></span>
* <span data-ttu-id="8c72f-117">Transformation für gemischte Realität mithilfe von Dritt-Rendering durch PV-Kamera.</span><span class="sxs-lookup"><span data-stu-id="8c72f-117">Mixed Reality Capture using 3rd eye rendering through PV camera.</span></span>
* <span data-ttu-id="8c72f-118">Unterstützt ["Play" in hololens 2 mit der Holographic Remoting-App](#holographic-remoting-in-unity-editor-play-mode), sodass Entwickler Skripts debuggen können, ohne auf dem Gerät zu entwickeln und bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="8c72f-118">Supports ["Play" to HoloLens 2 with the Holographic Remoting app](#holographic-remoting-in-unity-editor-play-mode), allowing developers to debug scripts without building and deploying to the device.</span></span>
* <span data-ttu-id="8c72f-119">Kompatibel mit mrtk Unity 2.5.3 und neuer über die [Unterstützung von mrtk openxr-Anbietern](openxr-getting-started.md#using-mrtk-with-openxr-support).</span><span class="sxs-lookup"><span data-stu-id="8c72f-119">Compatible with MRTK Unity 2.5.3 and newer through [MRTK OpenXR provider support](openxr-getting-started.md#using-mrtk-with-openxr-support).</span></span>
* <span data-ttu-id="8c72f-120">Kompatibel mit Unity [arfoundation 4,0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) oder höher.</span><span class="sxs-lookup"><span data-stu-id="8c72f-120">Compatible with Unity [ARFoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) or later.</span></span>
* <span data-ttu-id="8c72f-121">(In 0.1.3 hinzugefügt) Unterstützt die [Desktop-App Holographic Remoting](#holographic-remoting-in-desktop-app) aus einer erstellten und bereitgestellten eigenständigen Windows-app.</span><span class="sxs-lookup"><span data-stu-id="8c72f-121">(Added in 0.1.3) Supports [desktop app Holographic Remoting](#holographic-remoting-in-desktop-app) from a built and deployed Windows Standalone app.</span></span>
* <span data-ttu-id="8c72f-122">(In 0.1.4 hinzugefügt) Unterstützt die [QR-Code Überwachung](#qr-codes) auf HoloLens2 über spatialgraphnode</span><span class="sxs-lookup"><span data-stu-id="8c72f-122">(Added in 0.1.4) Supports [QR code tracking](#qr-codes) on HoloLens2 through SpatialGraphNode</span></span>

## <a name="holographic-remoting-setup"></a><span data-ttu-id="8c72f-123">Holographic Remoting-Setup</span><span class="sxs-lookup"><span data-stu-id="8c72f-123">Holographic Remoting setup</span></span>

1. <span data-ttu-id="8c72f-124">Zunächst müssen Sie [die Holographic Remoting Player-App](https://www.microsoft.com/store/productId/9NBLGGH4SV40) aus dem Microsoft Store auf den hololens 2 installieren.</span><span class="sxs-lookup"><span data-stu-id="8c72f-124">First, you need to [install the Holographic Remoting Player app](https://www.microsoft.com/store/productId/9NBLGGH4SV40) from the Microsoft Store on your HoloLens 2</span></span>
2. <span data-ttu-id="8c72f-125">Führen Sie die Holographic Remoting Player-App auf hololens 2 aus, und Sie sehen die Versionsnummer und IP-Adresse, mit der Sie eine Verbindung herstellen.</span><span class="sxs-lookup"><span data-stu-id="8c72f-125">Run the Holographic Remoting Player app on HoloLens 2 and you'll see the version number and IP address to connect to</span></span>
    * <span data-ttu-id="8c72f-126">Sie benötigen v 2.4 oder höher, um mit dem openxr-Plug-in zu arbeiten.</span><span class="sxs-lookup"><span data-stu-id="8c72f-126">You'll need v2.4 or later to work with the OpenXR plugin</span></span>

    ![Screenshot des Holographic-Remoting-Players, der in den hololens ausgeführt wird](images/openxr-features-img-01.png)

## <a name="holographic-remoting-in-unity-editor-play-mode"></a><span data-ttu-id="8c72f-128">Holographic-Remoting im Unity-Editor-Wiedergabemodus</span><span class="sxs-lookup"><span data-stu-id="8c72f-128">Holographic Remoting in Unity Editor play mode</span></span>

<span data-ttu-id="8c72f-129">Das Erstellen eines UWP Unity-Projekts in Visual Studio Project und das anschließende Verpacken und Bereitstellen des Projekts auf einem hololens 2-Gerät kann einige Zeit in Anspruch nehmen.</span><span class="sxs-lookup"><span data-stu-id="8c72f-129">Building a UWP Unity project in Visual Studio project and then packaging and deploying it to a HoloLens 2 device can take some time.</span></span> <span data-ttu-id="8c72f-130">Eine Lösung besteht darin, das Feature "Holographic Editor Remoting" zu aktivieren, mit dem Sie Ihr c#-Skript mit dem Modus "wiedergeben" direkt auf ein hololens 2-Gerät über Ihr Netzwerk Debuggen können.</span><span class="sxs-lookup"><span data-stu-id="8c72f-130">One solution is to enable the Holographic Editor Remoting feature, which lets you debug your C# script using “Play” mode directly to a HoloLens 2 device over your network.</span></span> <span data-ttu-id="8c72f-131">In diesem Szenario wird der Aufwand für das entwickeln und Bereitstellen eines UWP-Pakets auf dem Remote Gerät vermieden.</span><span class="sxs-lookup"><span data-stu-id="8c72f-131">This scenario avoids the overhead of building and deploying a UWP package to remote device.</span></span>

1. <span data-ttu-id="8c72f-132">Befolgen Sie die Schritte in [Holographic Remoting-Setup](#holographic-remoting-setup) .</span><span class="sxs-lookup"><span data-stu-id="8c72f-132">Follow the steps in [Holographic Remoting setup](#holographic-remoting-setup)</span></span>
2. <span data-ttu-id="8c72f-133">Öffnen Sie die **Projekteinstellungen für die > bearbeiten**, navigieren Sie zu der **XR-Plug-in-Verwaltung**, und aktivieren Sie das Kontrollkästchen **Windows Mixed Reality Feature Set** :</span><span class="sxs-lookup"><span data-stu-id="8c72f-133">Open **Edit -> Project Settings**, navigate to **XR plug-in Management**, and check the **Windows Mixed Reality feature set** box:</span></span>

    ![Screenshot des Bereichs "Projekteinstellungen" im Unity-Editor mit hervorgehobener XR-Plug-in-Verwaltung](images/openxr-features-img-02.png)

3. <span data-ttu-id="8c72f-135">Erweitern Sie unter **openxr** den Abschnitt **Features** , und wählen Sie **Alle anzeigen** aus.</span><span class="sxs-lookup"><span data-stu-id="8c72f-135">Expand the **Features** section under **OpenXR** and select **Show All**</span></span>
4. <span data-ttu-id="8c72f-136">Aktivieren Sie das Kontrollkästchen "Remoting" für das **Holographic Editor** , und geben Sie die IP-Adresse ein, die Sie aus der Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="8c72f-136">Check the **Holographic Editor Remoting** checkbox and input the IP address you get from the Holographic Remoting app:</span></span>

    ![Screenshot des Bereichs "Projekteinstellungen" im Unity-Editor mit hervorgehobenen Features](images/openxr-features-img-03.png)

<span data-ttu-id="8c72f-138">Nun können Sie auf die Schaltfläche "Wiedergabe" klicken, um Ihre Unity-app in der Holographic Remoting-App auf Ihren hololens wiederzugeben.</span><span class="sxs-lookup"><span data-stu-id="8c72f-138">Now you can click the “Play” button to play your Unity app into the Holographic Remoting app on your HoloLens.</span></span> <span data-ttu-id="8c72f-139">Sie können auch [Visual Studio an Unity anfügen](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) , um c#-Skripts im Wiedergabemodus zu debuggen.</span><span class="sxs-lookup"><span data-stu-id="8c72f-139">You can also [attach Visual Studio to Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) to debug C# scripts in the play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="8c72f-140">Ab Version 0.1.0 unterstützt die Holographic Remoting Runtime keine Anker, und aranchormanager-Funktionen können nicht durch Remoting verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="8c72f-140">As of version 0.1.0, the Holographic Remoting runtime doesn’t support Anchors, and ARAnchorManager functionalities will not work through remoting.</span></span>  <span data-ttu-id="8c72f-141">Diese Funktion wird in zukünftigen Versionen veröffentlicht.</span><span class="sxs-lookup"><span data-stu-id="8c72f-141">This feature is coming in future releases.</span></span>

## <a name="holographic-remoting-in-desktop-app"></a><span data-ttu-id="8c72f-142">Holographic Remoting in der Desktop-App</span><span class="sxs-lookup"><span data-stu-id="8c72f-142">Holographic Remoting in desktop app</span></span>

> [!NOTE]
> <span data-ttu-id="8c72f-143">Remoting-Unterstützung für eigenständige Windows-Apps wurde in der 0.1.3-Paketversion hinzugefügt</span><span class="sxs-lookup"><span data-stu-id="8c72f-143">Windows Standalone app remoting support was added in the 0.1.3 package release.</span></span>
> <span data-ttu-id="8c72f-144">Ab Version 0.1.3 unterstützt diese Funktion keine UWP-Builds.</span><span class="sxs-lookup"><span data-stu-id="8c72f-144">As of version 0.1.3, this feature doesn’t support UWP builds.</span></span>

1. <span data-ttu-id="8c72f-145">Befolgen Sie die Schritte in [Holographic Remoting-Setup](#holographic-remoting-setup) .</span><span class="sxs-lookup"><span data-stu-id="8c72f-145">Follow the steps in [Holographic Remoting setup](#holographic-remoting-setup)</span></span>
2. <span data-ttu-id="8c72f-146">Öffnen Sie die **Projekteinstellungen für die > bearbeiten**, navigieren Sie zu der **XR-Plug-in-Verwaltung**, und aktivieren Sie das Kontrollkästchen **Windows Mixed Reality Feature Set** .</span><span class="sxs-lookup"><span data-stu-id="8c72f-146">Open **Edit -> Project Settings**, navigate to **XR plug-in Management**, and check the **Windows Mixed Reality feature set** box.</span></span> <span data-ttu-id="8c72f-147">Deaktivieren Sie außerdem die Option " **XR beim Start initialisieren**":</span><span class="sxs-lookup"><span data-stu-id="8c72f-147">Also, uncheck **Initialize XR on Startup**:</span></span>

    ![Screenshot des Bereichs "Projekteinstellungen" im Unity-Editor geöffnet, bei dem "XR beim Start initialisieren" deaktiviert ist](images/openxr-features-img-02-app.png)

3. <span data-ttu-id="8c72f-149">Erweitern Sie unter **openxr** den Abschnitt **Features** , und wählen Sie **Alle anzeigen** aus.</span><span class="sxs-lookup"><span data-stu-id="8c72f-149">Expand the **Features** section under **OpenXR** and select **Show All**</span></span>
4. <span data-ttu-id="8c72f-150">Aktivieren Sie das Kontrollkästchen " **Holographic App Remoting** ":</span><span class="sxs-lookup"><span data-stu-id="8c72f-150">Check the **Holographic App Remoting** checkbox:</span></span>

    ![Screenshot des Bereichs "Projekteinstellungen" im Unity-Editor mit aktiviertem App-Remoting](images/openxr-features-img-03-app.png)

5. <span data-ttu-id="8c72f-152">Als nächstes schreiben Sie Code, um die Remotingkonfiguration und die Initialisierung von "XR</span><span class="sxs-lookup"><span data-stu-id="8c72f-152">Next, write some code to set the remoting configuration and trigger XR initialization.</span></span> <span data-ttu-id="8c72f-153">Die mit dem [Mixed Reality openxr-Plug](openxr-getting-started.md#hololens-2-samples) -in verteilte Beispiel-app enthält AppRemoting.cs, das ein Beispielszenario für das Herstellen einer Verbindung mit einer bestimmten IP-Adresse zur Laufzeit anzeigt.</span><span class="sxs-lookup"><span data-stu-id="8c72f-153">The sample app distributed with the [Mixed Reality OpenXR Plugin](openxr-getting-started.md#hololens-2-samples) contains AppRemoting.cs, which shows an example scenario for connecting to a specific IP address at runtime.</span></span> <span data-ttu-id="8c72f-154">Wenn Sie die Beispiel-APP an diesem Punkt auf einem lokalen Computer bereitstellen, wird ein Eingabefeld für die IP-Adresse mit der Schaltfläche Verbinden angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8c72f-154">Deploying the sample app to a local machine at this point will display an IP address input field with a connect button.</span></span> <span data-ttu-id="8c72f-155">Wenn Sie eine IP-Adresse eingeben und auf Verbinden klicken, wird XR initialisiert, und es wird versucht, eine Verbindung zum Zielgerät herzustellen</span><span class="sxs-lookup"><span data-stu-id="8c72f-155">Typing an IP address and clicking Connect will initialize XR and attempt to connect to the target device:</span></span>

    ![Screenshot der Beispiel-App mit Beispiel-App-Remoting-Benutzeroberfläche](images/openxr-sample-app-remoting.png)

6. <span data-ttu-id="8c72f-157">Um benutzerdefinierten Verbindungs Code zu schreiben, müssen Sie `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` mit einem ausgefüllten-Befehl aufzurufen `RemotingConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="8c72f-157">To write custom connection code, call `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` with a filled-in `RemotingConfiguration`.</span></span> <span data-ttu-id="8c72f-158">Die Beispiel-App macht dies im Inspektor verfügbar und zeigt, wie die IP-Adresse aus einem Textfeld ausgefüllt wird.</span><span class="sxs-lookup"><span data-stu-id="8c72f-158">The sample app exposes this in the inspector and shows how to fill in the IP address from a text field.</span></span> <span data-ttu-id="8c72f-159">Durch Aufrufen von `Connect` wird die Konfiguration festgelegt, und der XR wird automatisch initialisiert, weshalb Sie als Coroutine aufgerufen werden muss:</span><span class="sxs-lookup"><span data-stu-id="8c72f-159">Calling `Connect` will set the configuration and automatically initialize XR, which is why it must be called as a coroutine:</span></span>

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

7. <span data-ttu-id="8c72f-160">Während der Ausführung können Sie den aktuellen Verbindungsstatus mit der API abrufen und optional die Verbindung mit dem `AppRemoting.TryGetConnectionState` XR trennen und die Initialisierung mithilfe von aufheben `AppRemoting.Disconnect()` .</span><span class="sxs-lookup"><span data-stu-id="8c72f-160">While running, you can obtain the current connection state with the `AppRemoting.TryGetConnectionState` API, and optionally disconnect and de-initialize XR using `AppRemoting.Disconnect()`.</span></span> <span data-ttu-id="8c72f-161">Diese kann verwendet werden, um die Verbindung zu einem anderen Gerät innerhalb derselben App-Sitzung zu trennen und erneut eine Verbindung herzustellen.</span><span class="sxs-lookup"><span data-stu-id="8c72f-161">This could be used to disconnect and reconnect to a different device within the same app session.</span></span> <span data-ttu-id="8c72f-162">Die Beispiel-App bietet einen zu fügbaren Cube, der die Remote Sitzung trennt, wenn Sie getippt wird.</span><span class="sxs-lookup"><span data-stu-id="8c72f-162">The sample app provides a tappable cube which will disconnect the remoting session if tapped.</span></span>

### <a name="migration-from-previous-apis"></a><span data-ttu-id="8c72f-163">Migration von vorherigen APIs</span><span class="sxs-lookup"><span data-stu-id="8c72f-163">Migration from previous APIs</span></span>

#### <a name="unityenginexrwsaholographicremoting"></a><span data-ttu-id="8c72f-164">Unityengine. XR. WSA. holographikremoting</span><span class="sxs-lookup"><span data-stu-id="8c72f-164">UnityEngine.XR.WSA.HolographicRemoting</span></span>

<span data-ttu-id="8c72f-165">Aus dem Beispielcode für die [Unity-](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html)Dokumentation:</span><span class="sxs-lookup"><span data-stu-id="8c72f-165">From the sample code on [Unity's docs](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html):</span></span>

| <span data-ttu-id="8c72f-166">XR. WSA. Holographikremoting</span><span class="sxs-lookup"><span data-stu-id="8c72f-166">XR.WSA.HolographicRemoting</span></span> | <span data-ttu-id="8c72f-167">Openxr. Remoting. appremoting</span><span class="sxs-lookup"><span data-stu-id="8c72f-167">OpenXR.Remoting.AppRemoting</span></span> |
| ---- | ---- |
| `HolographicRemoting.Connect(String)` | `AppRemoting.Connect(RemotingConfiguration)` |
| `HolographicRemoting.ConnectionState` | `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `StartCoroutine(LoadDevice("WindowsMR"))`| <span data-ttu-id="8c72f-168">[N/v: automatisch beim Aufrufen von `AppRemoting.Connect` ]</span><span class="sxs-lookup"><span data-stu-id="8c72f-168">[N/A: Automatically happens when calling `AppRemoting.Connect`]</span></span>  |

#### <a name="unityenginexrwindowsmrwindowsmrremoting"></a><span data-ttu-id="8c72f-169">Unityengine. XR. windowsmr. windowsmrremoting</span><span class="sxs-lookup"><span data-stu-id="8c72f-169">UnityEngine.XR.WindowsMR.WindowsMRRemoting</span></span>

| <span data-ttu-id="8c72f-170">XR. Windowsmr. windowsmrremoting</span><span class="sxs-lookup"><span data-stu-id="8c72f-170">XR.WindowsMR.WindowsMRRemoting</span></span> | <span data-ttu-id="8c72f-171">Openxr. Remoting. appremoting</span><span class="sxs-lookup"><span data-stu-id="8c72f-171">OpenXR.Remoting.AppRemoting</span></span> |
| ---- | ---- |
| `WindowsMRRemoting.Connect()` | `AppRemoting.Connect(RemotingConfiguration)` |
| `WindowsMRRemoting.Disconnect()` | `AppRemoting.Disconnect()` |
| <span data-ttu-id="8c72f-172">`WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` und `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`</span><span class="sxs-lookup"><span data-stu-id="8c72f-172">`WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` and `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`</span></span>| `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| <span data-ttu-id="8c72f-173">`WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName`</span><span class="sxs-lookup"><span data-stu-id="8c72f-173">`WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName`</span></span> | <span data-ttu-id="8c72f-174">An `AppRemoting.Connect` über die Struktur übermittelt `RemotingConfiguration`</span><span class="sxs-lookup"><span data-stu-id="8c72f-174">Passed into `AppRemoting.Connect` via the `RemotingConfiguration` struct</span></span> |
| `WindowsMRRemoting.isConnected` | `AppRemoting.TryGetConnectionState(out ConnectionState state, out _) && state == ConnectionState.Connected`

## <a name="anchors-and-anchor-persistence"></a><span data-ttu-id="8c72f-175">Anker und Anker Persistenz</span><span class="sxs-lookup"><span data-stu-id="8c72f-175">Anchors and Anchor Persistence</span></span>

<span data-ttu-id="8c72f-176">Das Mixed Reality openxr-Plug-in stellt grundlegende Anker Funktionen durch eine Implementierung von Unity **aranchormanager** bereit.</span><span class="sxs-lookup"><span data-stu-id="8c72f-176">The Mixed Reality OpenXR Plugin supplies basic anchor functionality through an implementation of Unity’s ARFoundation **ARAnchorManager**.</span></span> <span data-ttu-id="8c72f-177">Informationen zu den Grundlagen von **aranchor** s in arfoundation finden Sie unter [arfoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span><span class="sxs-lookup"><span data-stu-id="8c72f-177">To learn the basics on **ARAnchor** s in ARFoundation, visit the [ARFoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span></span> <span data-ttu-id="8c72f-178">Ab Version 0.1.0 unterstützt dieses Plug-in alle aranchormanager-Funktionen außer der Erstellung von Ankern, die mit einer Ebene verbunden sind, die in einer zukünftigen Version verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="8c72f-178">As of version 0.1.0, this plugin supports all ARAnchorManager functionality except creating anchors attached to a plane, which is coming in a future release.</span></span>

### <a name="anchor-persistence-and-the-xranchorstore"></a><span data-ttu-id="8c72f-179">Anker Persistenz und xranchorstore</span><span class="sxs-lookup"><span data-stu-id="8c72f-179">Anchor Persistence and the XRAnchorStore</span></span>

<span data-ttu-id="8c72f-180">Eine zusätzliche API mit dem Namen " **xranchorstore** " ermöglicht, dass Anker zwischen Sitzungen beibehalten werden.</span><span class="sxs-lookup"><span data-stu-id="8c72f-180">An additional API called the **XRAnchorStore** enables anchors to be persisted between sessions.</span></span> <span data-ttu-id="8c72f-181">Der xranchorstore ist eine Darstellung der gespeicherten Anker auf Ihrem Gerät.</span><span class="sxs-lookup"><span data-stu-id="8c72f-181">The XRAnchorStore is a representation of the saved anchors on your device.</span></span> <span data-ttu-id="8c72f-182">Anker können von **aranchor** in der Unity-Szene persistent gespeichert, aus dem Speicher in neue **aranchor** geladen oder aus dem Speicher gelöscht werden.</span><span class="sxs-lookup"><span data-stu-id="8c72f-182">Anchors can be persisted from **ARAnchors** in the Unity scene, loaded from storage into new **ARAnchors**, or deleted from storage.</span></span>

> [!NOTE]
> <span data-ttu-id="8c72f-183">Diese Anker müssen auf demselben Gerät gespeichert und geladen werden.</span><span class="sxs-lookup"><span data-stu-id="8c72f-183">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="8c72f-184">Der Geräte übergreifende Anker Speicher wird in einer zukünftigen Version durch Azure Spatial Anchor unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8c72f-184">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

``` cs
public class Microsoft.MixedReality.ARSubsystems.XRAnchorStore
{
    // A list of all persisted anchors, which can be loaded.
    public IReadOnlyList<string> PersistedAnchorNames { get; }

    // Clear all persisted anchors
    public void Clear();

    // Load a single persisted anchor by name. The ARAnchorManager will create this new anchor and report it in
    // the ARAnchorManager.anchorsChanged event. The TrackableId returned here is the same TrackableId the
    // ARAnchor will have when it is instantiated.
    public TrackableId LoadAnchor(string name);

    // Attempts to persist an existing ARAnchor with the given TrackableId to the local store. Returns true if
    // the storage is successful, false otherwise.
    public bool TryPersistAnchor(string name, TrackableId trackableId);

    // Removes a single persisted anchor from the anchor store. This will not affect any ARAnchors in the Unity
    // scene, only the anchors in storage.
    public void UnpersistAnchor(string name);
}
```

<span data-ttu-id="8c72f-185">Zum Laden von xranchorstore stellt das Plug-in eine Erweiterungsmethode für das xranchorsubsystem bereit, das Subsystem von aranchormanager:</span><span class="sxs-lookup"><span data-stu-id="8c72f-185">To load the XRAnchorStore, the plugin provides an extension method on the XRAnchorSubsystem, the subsystem of an ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

<span data-ttu-id="8c72f-186">Um diese Erweiterungsmethode zu verwenden, greifen Sie über das Subsystem von aranchormanager wie folgt auf Sie zu:</span><span class="sxs-lookup"><span data-stu-id="8c72f-186">To use this extension method, access it from an ARAnchorManager's subsystem as follows:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

<span data-ttu-id="8c72f-187">Ein vollständiges Beispiel für das beibehalten/beibehalten von Ankern finden Sie unter Anker-> Anker Sample gameobject und AnchorsSample.cs Script in the [Mixed Reality openxr Plugin Sample Scene](openxr-getting-started.md#hololens-2-samples):</span><span class="sxs-lookup"><span data-stu-id="8c72f-187">To see a full example of persisting / unpersisting anchors, check out the Anchors -> Anchors Sample GameObject and AnchorsSample.cs script in the [Mixed Reality OpenXR Plugin Sample Scene](openxr-getting-started.md#hololens-2-samples):</span></span>

![Screenshot des Bereichs "Hierarchie" im Unity-Editor mit hervorgehobenem Anker Beispiel](images/openxr-features-img-04.png)

![Screenshot des Bereichs "Inspector" im Unity-Editor mit hervorgehobenem Anker Beispielskript](images/openxr-features-img-05.png)

## <a name="motion-controller-and-hand-interactions"></a><span data-ttu-id="8c72f-190">Bewegungs Controller und Hand Interaktionen</span><span class="sxs-lookup"><span data-stu-id="8c72f-190">Motion controller and hand interactions</span></span>

<span data-ttu-id="8c72f-191">Informationen zu den Grundlagen von Mixed Reality-Interaktionen in Unity finden Sie in der [Unity-Anleitung für](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html)Unity.</span><span class="sxs-lookup"><span data-stu-id="8c72f-191">To learn the basics about mixed reality interactions in Unity, visit the [Unity Manual for Unity XR Input](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html).</span></span> <span data-ttu-id="8c72f-192">In dieser Unity-Dokumentation werden die Zuordnungen von Controller spezifischen Eingaben zu stärker verallgemeinerbaren **inputfeatureusage** s behandelt, und es wird erläutert, wie verfügbare XR-Eingaben identifiziert und kategorisiert werden können, wie Daten aus diesen Eingaben gelesen werden und vieles mehr.</span><span class="sxs-lookup"><span data-stu-id="8c72f-192">This Unity documentation covers the mappings from controller-specific inputs to more generalizable **InputFeatureUsage** s, how available XR inputs can be identified and categorized, how to read data from these inputs, and more.</span></span>

<span data-ttu-id="8c72f-193">Das Mixed Reality openxr-Plug-in bietet zusätzliche Eingabe Interaktions Profile, die Standard **inputfeatureusage** s zugeordnet sind, wie im folgenden beschrieben:</span><span class="sxs-lookup"><span data-stu-id="8c72f-193">The Mixed Reality OpenXR Plugin provides additional input interaction profiles, mapped to standard **InputFeatureUsage** s as detailed below:</span></span>

| <span data-ttu-id="8c72f-194">Input featureusage</span><span class="sxs-lookup"><span data-stu-id="8c72f-194">InputFeatureUsage</span></span> | <span data-ttu-id="8c72f-195">HP-Reverb-G2-Controller (openxr)</span><span class="sxs-lookup"><span data-stu-id="8c72f-195">HP Reverb G2 Controller (OpenXR)</span></span> | <span data-ttu-id="8c72f-196">Hololens-Hand (openxr)</span><span class="sxs-lookup"><span data-stu-id="8c72f-196">HoloLens Hand (OpenXR)</span></span> |
| ---- | ---- | ---- |
| <span data-ttu-id="8c72f-197">primary2DAxis</span><span class="sxs-lookup"><span data-stu-id="8c72f-197">primary2DAxis</span></span> | <span data-ttu-id="8c72f-198">Steuern</span><span class="sxs-lookup"><span data-stu-id="8c72f-198">Joystick</span></span> | |
| <span data-ttu-id="8c72f-199">primary2DAxisClick</span><span class="sxs-lookup"><span data-stu-id="8c72f-199">primary2DAxisClick</span></span> | <span data-ttu-id="8c72f-200">Joystick Klick</span><span class="sxs-lookup"><span data-stu-id="8c72f-200">Joystick - Click</span></span> | |
| <span data-ttu-id="8c72f-201">Trigger (trigger)</span><span class="sxs-lookup"><span data-stu-id="8c72f-201">trigger</span></span> | <span data-ttu-id="8c72f-202">Trigger</span><span class="sxs-lookup"><span data-stu-id="8c72f-202">Trigger</span></span>  | |
| <span data-ttu-id="8c72f-203">Hand</span><span class="sxs-lookup"><span data-stu-id="8c72f-203">grip</span></span> | <span data-ttu-id="8c72f-204">Hand</span><span class="sxs-lookup"><span data-stu-id="8c72f-204">Grip</span></span> | <span data-ttu-id="8c72f-205">Luft tippen oder drücken</span><span class="sxs-lookup"><span data-stu-id="8c72f-205">Air tap or squeeze</span></span> |
| <span data-ttu-id="8c72f-206">primarybutton</span><span class="sxs-lookup"><span data-stu-id="8c72f-206">primaryButton</span></span> | <span data-ttu-id="8c72f-207">[X/A]-drücken</span><span class="sxs-lookup"><span data-stu-id="8c72f-207">[X/A] - Press</span></span> | <span data-ttu-id="8c72f-208">In die Luft tippen</span><span class="sxs-lookup"><span data-stu-id="8c72f-208">Air tap</span></span> |
| <span data-ttu-id="8c72f-209">secondarybutton</span><span class="sxs-lookup"><span data-stu-id="8c72f-209">secondaryButton</span></span> | <span data-ttu-id="8c72f-210">[J/B]-drücken</span><span class="sxs-lookup"><span data-stu-id="8c72f-210">[Y/B] - Press</span></span> | |
| <span data-ttu-id="8c72f-211">gripbutton</span><span class="sxs-lookup"><span data-stu-id="8c72f-211">gripButton</span></span> | <span data-ttu-id="8c72f-212">Ziehpunkt-drücken</span><span class="sxs-lookup"><span data-stu-id="8c72f-212">Grip - Press</span></span> | |
| <span data-ttu-id="8c72f-213">Triggerbutton</span><span class="sxs-lookup"><span data-stu-id="8c72f-213">triggerButton</span></span> | <span data-ttu-id="8c72f-214">Auslösung: Drücken Sie</span><span class="sxs-lookup"><span data-stu-id="8c72f-214">Trigger - Press</span></span> | |
| <span data-ttu-id="8c72f-215">-menubutton-</span><span class="sxs-lookup"><span data-stu-id="8c72f-215">menuButton</span></span> | <span data-ttu-id="8c72f-216">Menü</span><span class="sxs-lookup"><span data-stu-id="8c72f-216">Menu</span></span> | |

### <a name="aim-and-grip-poses"></a><span data-ttu-id="8c72f-217">Ziele und Zieh Punkt</span><span class="sxs-lookup"><span data-stu-id="8c72f-217">Aim and Grip Poses</span></span>

<span data-ttu-id="8c72f-218">Sie haben Zugriff auf zwei Gruppen von Posen durch openxr-Eingabe Interaktionen:</span><span class="sxs-lookup"><span data-stu-id="8c72f-218">You have access to two sets of poses through OpenXR input interactions:</span></span>

* <span data-ttu-id="8c72f-219">Der Ziehpunkt für das Rendern von Objekten in der Hand.</span><span class="sxs-lookup"><span data-stu-id="8c72f-219">The grip poses for rendering objects in the hand</span></span>
* <span data-ttu-id="8c72f-220">Das Ziel für den Verweis auf die Welt.</span><span class="sxs-lookup"><span data-stu-id="8c72f-220">The aim poses for pointing into the world.</span></span>

<span data-ttu-id="8c72f-221">Weitere Informationen zu diesem Entwurf und den Unterschieden zwischen den beiden Posen finden Sie in den [unter Pfaden für openxr Specification-Input](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).</span><span class="sxs-lookup"><span data-stu-id="8c72f-221">More information on this design and the differences between the two poses can be found in the [OpenXR Specification - Input Subpaths](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).</span></span>

<span data-ttu-id="8c72f-222">Die von den inputfeatureages **deviceposition**, **devicerotations**, **de vicevelocity** und **deviceangularvelocity** bereitgestellten Posen stellen die openxr-Zieh Punkt **Darstellung dar.**</span><span class="sxs-lookup"><span data-stu-id="8c72f-222">Poses supplied by the InputFeatureUsages **DevicePosition**, **DeviceRotation**, **DeviceVelocity**, and **DeviceAngularVelocity** all represent the OpenXR **grip** pose.</span></span> <span data-ttu-id="8c72f-223">Inputfeatureverwendungen im Zusammenhang mit Ziehpunkt-Posen werden in Unity- [Common-Ages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)definiert.</span><span class="sxs-lookup"><span data-stu-id="8c72f-223">InputFeatureUsages related to grip poses are defined in Unity’s [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html).</span></span>

<span data-ttu-id="8c72f-224">Die von der Eingabe **Funktion "pointerposition**", " **pointerrotation**", " **pointervelocity**" und " **pointerangularvelocity** " bereitgestellten Posen stellen das openxr- **Ziel** dar.</span><span class="sxs-lookup"><span data-stu-id="8c72f-224">Poses supplied by the InputFeatureUsages **PointerPosition**, **PointerRotation**, **PointerVelocity**, and **PointerAngularVelocity** all represent the OpenXR **aim** pose.</span></span> <span data-ttu-id="8c72f-225">Diese inputfeatureusages sind nicht in enthaltenen c#-Dateien definiert, daher müssen Sie Ihre eigene inputfeatureusages wie folgt definieren:</span><span class="sxs-lookup"><span data-stu-id="8c72f-225">These InputFeatureUsages aren't defined in any included C# files, so you'll need to define your own InputFeatureUsages as follows:</span></span>

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

### <a name="haptics"></a><span data-ttu-id="8c72f-226">Haptik</span><span class="sxs-lookup"><span data-stu-id="8c72f-226">Haptics</span></span>

<span data-ttu-id="8c72f-227">Informationen zur Verwendung von Haptik im XR-Eingabe System von Unity finden Sie im [Unity-Handbuch für Unity-Eingabe-und-Haptik](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).</span><span class="sxs-lookup"><span data-stu-id="8c72f-227">For information on using haptics in Unity’s XR Input system, documentation can be found at the [Unity Manual for Unity XR Input - Haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).</span></span>

## <a name="qr-codes"></a><span data-ttu-id="8c72f-228">QR-Codes</span><span class="sxs-lookup"><span data-stu-id="8c72f-228">QR codes</span></span>

<span data-ttu-id="8c72f-229">HoloLens 2 kann QR-Codes in der Umgebung um das Headset erkennen und ein Koordinatensystem an der Position jedes Codes in der realen Welt einrichten.</span><span class="sxs-lookup"><span data-stu-id="8c72f-229">HoloLens 2 can detect QR codes in the environment around the headset, establishing a coordinate system at each code's real-world location.</span></span> <span data-ttu-id="8c72f-230">Weitere Informationen finden Sie in der Dokumentation zur [QR-Code](../platform-capabilities-and-apis/qr-code-tracking.md) -Nachverfolgung.</span><span class="sxs-lookup"><span data-stu-id="8c72f-230">You can find more details in our [QR code tracking](../platform-capabilities-and-apis/qr-code-tracking.md) documentation.</span></span>  <span data-ttu-id="8c72f-231">Wenn Sie das openxr-Plug-in verwenden, rufen Sie den [ `SpatialGraphNodeId` von der QR-API ab](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference) , und verwenden `Microsoft.MixedReality.OpenXR.SpatialGraphNode` Sie die API zum Suchen des QR-Codes</span><span class="sxs-lookup"><span data-stu-id="8c72f-231">When using the OpenXR plugin, grab the [`SpatialGraphNodeId` from the QR API](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference) and use the `Microsoft.MixedReality.OpenXR.SpatialGraphNode` API to locate the QR code.</span></span>

<span data-ttu-id="8c72f-232">Als Referenz haben wir ein [Beispiel Projekt für QR-Nachverfolgung auf GitHub](https://github.com/yl-msft/QRTracking) mit einer ausführlicheren Verwendungs Erklärung für die [ `SpatialGraphNode` API](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs).</span><span class="sxs-lookup"><span data-stu-id="8c72f-232">For reference, we have a [QR tracking sample project on GitHub](https://github.com/yl-msft/QRTracking) with more a detailed usage explanation for the [`SpatialGraphNode` API](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs).</span></span>

## <a name="whats-coming-soon"></a><span data-ttu-id="8c72f-233">Bald verfügbar</span><span class="sxs-lookup"><span data-stu-id="8c72f-233">What's coming soon</span></span>

<span data-ttu-id="8c72f-234">Die folgenden Probleme und fehlenden Features sind mit der **Version 0.1.0** des openxr-Plug-ins von Mixed Reality bekannt.</span><span class="sxs-lookup"><span data-stu-id="8c72f-234">The following issues and missing features are known with Mixed Reality OpenXR plugin **version 0.1.0**.</span></span> <span data-ttu-id="8c72f-235">Wir arbeiten an diesen und veröffentlichen Korrekturen und neue Features in zukünftigen Versionen.</span><span class="sxs-lookup"><span data-stu-id="8c72f-235">We're working on these and will release fixes and new features in upcoming releases.</span></span>

* <span data-ttu-id="8c72f-236">**Arplanesubsystem** wird noch nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8c72f-236">**ARPlaneSubsystem** is not supported yet.</span></span> <span data-ttu-id="8c72f-237">**Arplanemanager**, **arraycastmanager** und verwandte APIs wie **aranchormanager. attachanchor** werden auf hololens 2 ebenfalls nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8c72f-237">**ARPlaneManager**, **ARRaycastManager**, and related API like **ARAnchorManager.AttachAnchor** are also not supported on HoloLens 2.</span></span>
* <span data-ttu-id="8c72f-238">Die **Anker Persistenz** wird von Holographic Remoting noch nicht unterstützt, aber in naher Zukunft.</span><span class="sxs-lookup"><span data-stu-id="8c72f-238">**Anchor persistence** isn't supported by Holographic Remoting yet, but it's coming in the near future.</span></span>
* <span data-ttu-id="8c72f-239">**Hand Mesh** -Nachverfolgung und **xrmeshsubsystem** werden noch nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8c72f-239">**Hand Mesh** tracking and **XRMeshSubsystem** aren't supported yet.</span></span>
* <span data-ttu-id="8c72f-240">Die Unterstützung von **räumlichen Azure-Ankern** wird in einer zukünftigen Version angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8c72f-240">**Azure Spatial Anchors** support is coming in a future release.</span></span>
* <span data-ttu-id="8c72f-241">**ARM64** ist die einzige unterstützte Plattform für hololens 2-apps.</span><span class="sxs-lookup"><span data-stu-id="8c72f-241">**ARM64** is the only supported platform for HoloLens 2 apps.</span></span> <span data-ttu-id="8c72f-242">Die **Arm** -Plattform wird in einer zukünftigen Version angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8c72f-242">The **ARM** platform is coming in a future release.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="8c72f-243">Problembehandlung</span><span class="sxs-lookup"><span data-stu-id="8c72f-243">Troubleshooting</span></span>

<span data-ttu-id="8c72f-244">Wenn Sie eine Unity-App auf hololens 2 aussetzen und fortsetzen, kann die APP nicht ordnungsgemäß fortgesetzt werden, was zu vier Drehungs Punkten in der hololens-Ansicht führt.</span><span class="sxs-lookup"><span data-stu-id="8c72f-244">When you suspend and resume a Unity app on HoloLens 2, the app can't correctly resume, which leads to 4 spinning dots in the HoloLens view.</span></span>

* <span data-ttu-id="8c72f-245">Festlegen des tiefen Übermittlungs **Modus** auf " **None** " in den openxr-Projekteinstellungen als Problem Umgehung</span><span class="sxs-lookup"><span data-stu-id="8c72f-245">Set **Depth submission Mode** to **None** in the OpenXR project settings as a workaround</span></span>
