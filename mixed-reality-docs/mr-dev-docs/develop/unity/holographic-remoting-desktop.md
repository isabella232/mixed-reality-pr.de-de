---
title: Holographic Remoting in der Desktop-App
description: Erfahren Sie, wie Sie Holographic Remoting in einer Desktop-App mit OpenXR verwenden.
author: hferrone
ms.author: alexturn
ms.date: 03/16/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, Augmented Reality, Virtual Reality, Mixed Reality-Headsets, Lernen, Tutorial, Erste Schritte, holografisches Remoting, Desktop
ms.openlocfilehash: 18557af1f08ea05715b92b5072460871bb05a329
ms.sourcegitcommit: b195b82f7e83e2ac4f5d8937d169e9dcb865d46d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2021
ms.locfileid: "110333414"
---
# <a name="holographic-remoting-in-desktop-app"></a><span data-ttu-id="6823c-104">Holographic Remoting in der Desktop-App</span><span class="sxs-lookup"><span data-stu-id="6823c-104">Holographic Remoting in desktop app</span></span>

> [!NOTE]
> <span data-ttu-id="6823c-105">Die Remotingunterstützung für eigenständige Windows-Apps wurde in der Paketversion 0.1.3 hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="6823c-105">Windows Standalone app remoting support was added in the 0.1.3 package release.</span></span>
> <span data-ttu-id="6823c-106">Ab Version 0.1.3 unterstützt dieses Feature keine UWP-Builds.</span><span class="sxs-lookup"><span data-stu-id="6823c-106">As of version 0.1.3, this feature doesn’t support UWP builds.</span></span>

1. <span data-ttu-id="6823c-107">Führen Sie die Schritte unter [Holographic Remoting setup (Holographic Remoting-Setup) aus.](unity-play-mode.md#holographic-remoting-setup)</span><span class="sxs-lookup"><span data-stu-id="6823c-107">Follow the steps in [Holographic Remoting setup](unity-play-mode.md#holographic-remoting-setup)</span></span>
2. <span data-ttu-id="6823c-108">Öffnen **Sie Bearbeiten -> Projekteinstellungen,** navigieren Sie zu **XR-Plug-In-Verwaltung,** und aktivieren Sie **Windows Mixed Reality Featuresatz.**</span><span class="sxs-lookup"><span data-stu-id="6823c-108">Open **Edit -> Project Settings**, navigate to **XR plug-in Management**, and check the **Windows Mixed Reality feature set** box.</span></span> <span data-ttu-id="6823c-109">Deaktivieren Sie außerdem Initialize **XR on Startup (XR beim Start initialisieren):**</span><span class="sxs-lookup"><span data-stu-id="6823c-109">Also, uncheck **Initialize XR on Startup**:</span></span>

    ![Screenshot des im Unity-Editor geöffneten Fensters "Projekteinstellungen" mit deaktivierter Option "XR beim Start initialisieren"](images/openxr-features-img-02-app.png)

3. <span data-ttu-id="6823c-111">Erweitern Sie den **Abschnitt Features** unter **OpenXR, und** wählen Sie Alle anzeigen **aus.**</span><span class="sxs-lookup"><span data-stu-id="6823c-111">Expand the **Features** section under **OpenXR** and select **Show All**</span></span>
4. <span data-ttu-id="6823c-112">Aktivieren Sie **das Kontrollkästchen Holographic App Remoting:**</span><span class="sxs-lookup"><span data-stu-id="6823c-112">Check the **Holographic App Remoting** checkbox:</span></span>

    ![Screenshot: Bereich "Projekteinstellungen" im Unity-Editor mit aktivierter App-Remoting](images/openxr-features-img-03-app.png)

5. <span data-ttu-id="6823c-114">Schreiben Sie als Nächstes Code, um die Remotingkonfiguration zu konfigurieren und die XR-Initialisierung auszulösen.</span><span class="sxs-lookup"><span data-stu-id="6823c-114">Next, write some code to set the remoting configuration and trigger XR initialization.</span></span> <span data-ttu-id="6823c-115">Die Beispiel-App, die mit dem [Mixed Reality OpenXR-Plug-In](openxr-getting-started.md#unity-sample-projects-for-openxr-and-hololens-2) verteilt wird, enthält AppRemoting.cs. Dies zeigt ein Beispielszenario für das Herstellen einer Verbindung mit einer bestimmten IP-Adresse zur Laufzeit.</span><span class="sxs-lookup"><span data-stu-id="6823c-115">The sample app distributed with the [Mixed Reality OpenXR Plugin](openxr-getting-started.md#unity-sample-projects-for-openxr-and-hololens-2) contains AppRemoting.cs, which shows an example scenario for connecting to a specific IP address at runtime.</span></span> <span data-ttu-id="6823c-116">Wenn Sie die Beispiel-App an diesem Punkt auf einem lokalen Computer bereitstellen, wird ein Eingabefeld für die IP-Adresse mit einer Schaltfläche "Verbinden" angezeigt.</span><span class="sxs-lookup"><span data-stu-id="6823c-116">Deploying the sample app to a local machine at this point will display an IP address input field with a connect button.</span></span> <span data-ttu-id="6823c-117">Wenn Sie eine IP-Adresse eingeben und auf Verbinden klicken, wird XR initialisiert und versucht, eine Verbindung mit dem Zielgerät herzustellen:</span><span class="sxs-lookup"><span data-stu-id="6823c-117">Typing an IP address and clicking Connect will initialize XR and attempt to connect to the target device:</span></span>

    ![Screenshot der Beispiel-App mit Beispiel-App-Remoting-Benutzeroberfläche](images/openxr-sample-app-remoting.png)

6. <span data-ttu-id="6823c-119">Um benutzerdefinierten Verbindungscode zu schreiben, rufen `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` Sie mit einem ausgefüllten `RemotingConfiguration` auf.</span><span class="sxs-lookup"><span data-stu-id="6823c-119">To write custom connection code, call `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` with a filled-in `RemotingConfiguration`.</span></span> <span data-ttu-id="6823c-120">Die Beispiel-App macht dies im Inspektor verfügbar und zeigt, wie sie die IP-Adresse aus einem Textfeld einfüllt.</span><span class="sxs-lookup"><span data-stu-id="6823c-120">The sample app exposes this in the inspector and shows how to fill in the IP address from a text field.</span></span> <span data-ttu-id="6823c-121">Durch Aufrufen von wird die Konfiguration festgelegt und XR automatisch initialisiert. Aus diesem Grund muss `Connect` XR als Coroutine aufgerufen werden:</span><span class="sxs-lookup"><span data-stu-id="6823c-121">Calling `Connect` will set the configuration and automatically initialize XR, which is why it must be called as a coroutine:</span></span>

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

7. <span data-ttu-id="6823c-122">Während der Ausführung können Sie den aktuellen Verbindungsstatus mit der API abrufen und optional XR mit trennen `AppRemoting.TryGetConnectionState` und `AppRemoting.Disconnect()` initialisieren.</span><span class="sxs-lookup"><span data-stu-id="6823c-122">While running, you can obtain the current connection state with the `AppRemoting.TryGetConnectionState` API, and optionally disconnect and de-initialize XR using `AppRemoting.Disconnect()`.</span></span> <span data-ttu-id="6823c-123">Dies kann verwendet werden, um die Verbindung mit einem anderen Gerät innerhalb derselben App-Sitzung zu trennen und erneut herzustellen.</span><span class="sxs-lookup"><span data-stu-id="6823c-123">This could be used to disconnect and reconnect to a different device within the same app session.</span></span> <span data-ttu-id="6823c-124">Die Beispiel-App stellt einen Cube bereit, der die Remotingsitzung trennt, wenn darauf getippt wird.</span><span class="sxs-lookup"><span data-stu-id="6823c-124">The sample app provides a tappable cube which will disconnect the remoting session if tapped.</span></span>

### <a name="migration-from-previous-apis"></a><span data-ttu-id="6823c-125">Migration von vorherigen APIs</span><span class="sxs-lookup"><span data-stu-id="6823c-125">Migration from previous APIs</span></span>

#### <a name="unityenginexrwsaholographicremoting"></a><span data-ttu-id="6823c-126">UnityEngine.XR.WSA.HolographicRemoting</span><span class="sxs-lookup"><span data-stu-id="6823c-126">UnityEngine.XR.WSA.HolographicRemoting</span></span>

<span data-ttu-id="6823c-127">Aus dem Beispielcode in [der Unity-Dokumentation:](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html)</span><span class="sxs-lookup"><span data-stu-id="6823c-127">From the sample code on [Unity's docs](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html):</span></span>

| <span data-ttu-id="6823c-128">Xr. WSA. HolographicRemoting</span><span class="sxs-lookup"><span data-stu-id="6823c-128">XR.WSA.HolographicRemoting</span></span> | <span data-ttu-id="6823c-129">OpenXR.Remoting.AppRemoting</span><span class="sxs-lookup"><span data-stu-id="6823c-129">OpenXR.Remoting.AppRemoting</span></span> |
| ---- | ---- |
| `HolographicRemoting.Connect(String)` | `AppRemoting.Connect(RemotingConfiguration)` |
| `HolographicRemoting.ConnectionState` | `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `StartCoroutine(LoadDevice("WindowsMR"))`| <span data-ttu-id="6823c-130">[N/A: Wird automatisch beim Aufrufen von `AppRemoting.Connect` ]</span><span class="sxs-lookup"><span data-stu-id="6823c-130">[N/A: Automatically happens when calling `AppRemoting.Connect`]</span></span>  |

#### <a name="unityenginexrwindowsmrwindowsmrremoting"></a><span data-ttu-id="6823c-131">UnityEngine.XR.WindowsMR.WindowsMRRemoting</span><span class="sxs-lookup"><span data-stu-id="6823c-131">UnityEngine.XR.WindowsMR.WindowsMRRemoting</span></span>

| <span data-ttu-id="6823c-132">Xr. WindowsMR.WindowsMRRemoting</span><span class="sxs-lookup"><span data-stu-id="6823c-132">XR.WindowsMR.WindowsMRRemoting</span></span> | <span data-ttu-id="6823c-133">OpenXR.Remoting.AppRemoting</span><span class="sxs-lookup"><span data-stu-id="6823c-133">OpenXR.Remoting.AppRemoting</span></span> |
| ---- | ---- |
| `WindowsMRRemoting.Connect()` | `AppRemoting.Connect(RemotingConfiguration)` |
| `WindowsMRRemoting.Disconnect()` | `AppRemoting.Disconnect()` |
| <span data-ttu-id="6823c-134">`WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` und `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`</span><span class="sxs-lookup"><span data-stu-id="6823c-134">`WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` and `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`</span></span>| `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| <span data-ttu-id="6823c-135">`WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName`</span><span class="sxs-lookup"><span data-stu-id="6823c-135">`WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName`</span></span> | <span data-ttu-id="6823c-136">Übergeben an `AppRemoting.Connect` über die `RemotingConfiguration` -Struktur</span><span class="sxs-lookup"><span data-stu-id="6823c-136">Passed into `AppRemoting.Connect` via the `RemotingConfiguration` struct</span></span> |
| `WindowsMRRemoting.isConnected` | `AppRemoting.TryGetConnectionState(out ConnectionState state, out _) && state == ConnectionState.Connected`