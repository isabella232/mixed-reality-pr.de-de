---
title: Holographic Remoting in der Desktop-App
description: Erfahren Sie, wie Sie Holographic Remoting in einer Desktop-App mit openxr verwenden können.
author: hferrone
ms.author: alexturn
ms.date: 03/16/2021
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, Mixed Reality, mrtk, Mixed Reality Toolkit, Augmented Reality, Virtual Reality, Mixed Reality-Headsets, erlernen, Tutorial, Getting Started, Holographic Remoting, Desktop
ms.openlocfilehash: f3cf43d59b74b0f47e701acc1d7312544867b0df
ms.sourcegitcommit: d5e4eb94c87b86a7774a639f11cd9e35a7050107
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2021
ms.locfileid: "103624319"
---
# <a name="holographic-remoting-in-desktop-app"></a><span data-ttu-id="06ae1-104">Holographic Remoting in der Desktop-App</span><span class="sxs-lookup"><span data-stu-id="06ae1-104">Holographic Remoting in desktop app</span></span>

> [!NOTE]
> <span data-ttu-id="06ae1-105">Remoting-Unterstützung für eigenständige Windows-Apps wurde in der 0.1.3-Paketversion hinzugefügt</span><span class="sxs-lookup"><span data-stu-id="06ae1-105">Windows Standalone app remoting support was added in the 0.1.3 package release.</span></span>
> <span data-ttu-id="06ae1-106">Ab Version 0.1.3 unterstützt diese Funktion keine UWP-Builds.</span><span class="sxs-lookup"><span data-stu-id="06ae1-106">As of version 0.1.3, this feature doesn’t support UWP builds.</span></span>

1. <span data-ttu-id="06ae1-107">Befolgen Sie die Schritte in [Holographic Remoting-Setup](openxr-supported-features.md#holographic-remoting-setup) .</span><span class="sxs-lookup"><span data-stu-id="06ae1-107">Follow the steps in [Holographic Remoting setup](openxr-supported-features.md#holographic-remoting-setup)</span></span>
2. <span data-ttu-id="06ae1-108">Öffnen Sie die **Projekteinstellungen für die > bearbeiten**, navigieren Sie zu der **XR-Plug-in-Verwaltung**, und aktivieren Sie das Kontrollkästchen **Windows Mixed Reality Feature Set** .</span><span class="sxs-lookup"><span data-stu-id="06ae1-108">Open **Edit -> Project Settings**, navigate to **XR plug-in Management**, and check the **Windows Mixed Reality feature set** box.</span></span> <span data-ttu-id="06ae1-109">Deaktivieren Sie außerdem die Option " **XR beim Start initialisieren**":</span><span class="sxs-lookup"><span data-stu-id="06ae1-109">Also, uncheck **Initialize XR on Startup**:</span></span>

    ![Screenshot des Bereichs "Projekteinstellungen" im Unity-Editor geöffnet, bei dem "XR beim Start initialisieren" deaktiviert ist](images/openxr-features-img-02-app.png)

3. <span data-ttu-id="06ae1-111">Erweitern Sie unter **openxr** den Abschnitt **Features** , und wählen Sie **Alle anzeigen** aus.</span><span class="sxs-lookup"><span data-stu-id="06ae1-111">Expand the **Features** section under **OpenXR** and select **Show All**</span></span>
4. <span data-ttu-id="06ae1-112">Aktivieren Sie das Kontrollkästchen " **Holographic App Remoting** ":</span><span class="sxs-lookup"><span data-stu-id="06ae1-112">Check the **Holographic App Remoting** checkbox:</span></span>

    ![Screenshot des Bereichs "Projekteinstellungen" im Unity-Editor mit aktiviertem App-Remoting](images/openxr-features-img-03-app.png)

5. <span data-ttu-id="06ae1-114">Als nächstes schreiben Sie Code, um die Remotingkonfiguration und die Initialisierung von "XR</span><span class="sxs-lookup"><span data-stu-id="06ae1-114">Next, write some code to set the remoting configuration and trigger XR initialization.</span></span> <span data-ttu-id="06ae1-115">Die mit dem [Mixed Reality openxr-Plug](openxr-getting-started.md#hololens-2-samples) -in verteilte Beispiel-app enthält AppRemoting.cs, das ein Beispielszenario für das Herstellen einer Verbindung mit einer bestimmten IP-Adresse zur Laufzeit anzeigt.</span><span class="sxs-lookup"><span data-stu-id="06ae1-115">The sample app distributed with the [Mixed Reality OpenXR Plugin](openxr-getting-started.md#hololens-2-samples) contains AppRemoting.cs, which shows an example scenario for connecting to a specific IP address at runtime.</span></span> <span data-ttu-id="06ae1-116">Wenn Sie die Beispiel-APP an diesem Punkt auf einem lokalen Computer bereitstellen, wird ein Eingabefeld für die IP-Adresse mit der Schaltfläche Verbinden angezeigt.</span><span class="sxs-lookup"><span data-stu-id="06ae1-116">Deploying the sample app to a local machine at this point will display an IP address input field with a connect button.</span></span> <span data-ttu-id="06ae1-117">Wenn Sie eine IP-Adresse eingeben und auf Verbinden klicken, wird XR initialisiert, und es wird versucht, eine Verbindung zum Zielgerät herzustellen</span><span class="sxs-lookup"><span data-stu-id="06ae1-117">Typing an IP address and clicking Connect will initialize XR and attempt to connect to the target device:</span></span>

    ![Screenshot der Beispiel-App mit Beispiel-App-Remoting-Benutzeroberfläche](images/openxr-sample-app-remoting.png)

6. <span data-ttu-id="06ae1-119">Um benutzerdefinierten Verbindungs Code zu schreiben, müssen Sie `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` mit einem ausgefüllten-Befehl aufzurufen `RemotingConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="06ae1-119">To write custom connection code, call `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` with a filled-in `RemotingConfiguration`.</span></span> <span data-ttu-id="06ae1-120">Die Beispiel-App macht dies im Inspektor verfügbar und zeigt, wie die IP-Adresse aus einem Textfeld ausgefüllt wird.</span><span class="sxs-lookup"><span data-stu-id="06ae1-120">The sample app exposes this in the inspector and shows how to fill in the IP address from a text field.</span></span> <span data-ttu-id="06ae1-121">Durch Aufrufen von `Connect` wird die Konfiguration festgelegt, und der XR wird automatisch initialisiert, weshalb Sie als Coroutine aufgerufen werden muss:</span><span class="sxs-lookup"><span data-stu-id="06ae1-121">Calling `Connect` will set the configuration and automatically initialize XR, which is why it must be called as a coroutine:</span></span>

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

7. <span data-ttu-id="06ae1-122">Während der Ausführung können Sie den aktuellen Verbindungsstatus mit der API abrufen und optional die Verbindung mit dem `AppRemoting.TryGetConnectionState` XR trennen und die Initialisierung mithilfe von aufheben `AppRemoting.Disconnect()` .</span><span class="sxs-lookup"><span data-stu-id="06ae1-122">While running, you can obtain the current connection state with the `AppRemoting.TryGetConnectionState` API, and optionally disconnect and de-initialize XR using `AppRemoting.Disconnect()`.</span></span> <span data-ttu-id="06ae1-123">Diese kann verwendet werden, um die Verbindung zu einem anderen Gerät innerhalb derselben App-Sitzung zu trennen und erneut eine Verbindung herzustellen.</span><span class="sxs-lookup"><span data-stu-id="06ae1-123">This could be used to disconnect and reconnect to a different device within the same app session.</span></span> <span data-ttu-id="06ae1-124">Die Beispiel-App bietet einen zu fügbaren Cube, der die Remote Sitzung trennt, wenn Sie getippt wird.</span><span class="sxs-lookup"><span data-stu-id="06ae1-124">The sample app provides a tappable cube which will disconnect the remoting session if tapped.</span></span>

### <a name="migration-from-previous-apis"></a><span data-ttu-id="06ae1-125">Migration von vorherigen APIs</span><span class="sxs-lookup"><span data-stu-id="06ae1-125">Migration from previous APIs</span></span>

#### <a name="unityenginexrwsaholographicremoting"></a><span data-ttu-id="06ae1-126">Unityengine. XR. WSA. holographikremoting</span><span class="sxs-lookup"><span data-stu-id="06ae1-126">UnityEngine.XR.WSA.HolographicRemoting</span></span>

<span data-ttu-id="06ae1-127">Aus dem Beispielcode für die [Unity-](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html)Dokumentation:</span><span class="sxs-lookup"><span data-stu-id="06ae1-127">From the sample code on [Unity's docs](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html):</span></span>

| <span data-ttu-id="06ae1-128">XR. WSA. Holographikremoting</span><span class="sxs-lookup"><span data-stu-id="06ae1-128">XR.WSA.HolographicRemoting</span></span> | <span data-ttu-id="06ae1-129">Openxr. Remoting. appremoting</span><span class="sxs-lookup"><span data-stu-id="06ae1-129">OpenXR.Remoting.AppRemoting</span></span> |
| ---- | ---- |
| `HolographicRemoting.Connect(String)` | `AppRemoting.Connect(RemotingConfiguration)` |
| `HolographicRemoting.ConnectionState` | `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `StartCoroutine(LoadDevice("WindowsMR"))`| <span data-ttu-id="06ae1-130">[N/v: automatisch beim Aufrufen von `AppRemoting.Connect` ]</span><span class="sxs-lookup"><span data-stu-id="06ae1-130">[N/A: Automatically happens when calling `AppRemoting.Connect`]</span></span>  |

#### <a name="unityenginexrwindowsmrwindowsmrremoting"></a><span data-ttu-id="06ae1-131">Unityengine. XR. windowsmr. windowsmrremoting</span><span class="sxs-lookup"><span data-stu-id="06ae1-131">UnityEngine.XR.WindowsMR.WindowsMRRemoting</span></span>

| <span data-ttu-id="06ae1-132">XR. Windowsmr. windowsmrremoting</span><span class="sxs-lookup"><span data-stu-id="06ae1-132">XR.WindowsMR.WindowsMRRemoting</span></span> | <span data-ttu-id="06ae1-133">Openxr. Remoting. appremoting</span><span class="sxs-lookup"><span data-stu-id="06ae1-133">OpenXR.Remoting.AppRemoting</span></span> |
| ---- | ---- |
| `WindowsMRRemoting.Connect()` | `AppRemoting.Connect(RemotingConfiguration)` |
| `WindowsMRRemoting.Disconnect()` | `AppRemoting.Disconnect()` |
| <span data-ttu-id="06ae1-134">`WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` und `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`</span><span class="sxs-lookup"><span data-stu-id="06ae1-134">`WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` and `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`</span></span>| `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| <span data-ttu-id="06ae1-135">`WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName`</span><span class="sxs-lookup"><span data-stu-id="06ae1-135">`WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName`</span></span> | <span data-ttu-id="06ae1-136">An `AppRemoting.Connect` über die Struktur übermittelt `RemotingConfiguration`</span><span class="sxs-lookup"><span data-stu-id="06ae1-136">Passed into `AppRemoting.Connect` via the `RemotingConfiguration` struct</span></span> |
| `WindowsMRRemoting.isConnected` | `AppRemoting.TryGetConnectionState(out ConnectionState state, out _) && state == ConnectionState.Connected`