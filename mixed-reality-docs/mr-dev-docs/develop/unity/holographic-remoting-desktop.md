---
title: Holographic Remoting in der Desktop-App
description: Erfahren Sie, wie Sie Holographic Remoting in einer Desktop-App mit OpenXR verwenden.
author: hferrone
ms.author: alexturn
ms.date: 03/16/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, Augmented Reality, Virtual Reality, Mixed Reality-Headsets, Lernen, Tutorial, Erste Schritte, holografisches Remoting, Desktop
ms.openlocfilehash: b04f7e003cff41ae6970bef71c37231b2475ca75
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906726"
---
# <a name="holographic-remoting-in-desktop-app"></a>Holographic Remoting in der Desktop-App

> [!NOTE]
> Die Remotingunterstützung für eigenständige Windows-Apps wurde in der Paketversion 0.1.3 hinzugefügt.
> Ab Version 0.1.3 unterstützt dieses Feature keine UWP-Builds.

1. Führen Sie die Schritte unter [Holographic Remoting setup (Holographic Remoting-Setup) aus.](unity-play-mode.md#holographic-remoting-setup)
2. Öffnen **Sie Bearbeiten -> Projekteinstellungen,** navigieren Sie zu **XR-Plug-In-Verwaltung,** und aktivieren Sie **Windows Mixed Reality Featuresatz.** Deaktivieren Sie außerdem Initialize **XR on Startup (XR beim Start initialisieren):**

    ![Screenshot des im Unity-Editor geöffneten Fensters "Projekteinstellungen" mit deaktivierter Option "XR beim Start initialisieren"](images/openxr-features-img-02-app.png)

3. Erweitern Sie den **Abschnitt Features** unter **OpenXR, und** wählen Sie Alle anzeigen **aus.**
4. Aktivieren Sie **das Kontrollkästchen Holographic App Remoting:**

    ![Screenshot: Bereich "Projekteinstellungen" im Unity-Editor mit aktivierter App-Remoting](images/openxr-features-img-03-app.png)

5. Schreiben Sie als Nächstes Code, um die Remotingkonfiguration zu konfigurieren und die XR-Initialisierung auszulösen. Die Beispiel-App, die mit dem [Mixed Reality OpenXR-Plug-In](./xr-project-setup.md#unity-sample-projects-for-openxr-and-hololens-2) verteilt wird, enthält AppRemoting.cs. Dies zeigt ein Beispielszenario für das Herstellen einer Verbindung mit einer bestimmten IP-Adresse zur Laufzeit. Wenn Sie die Beispiel-App an diesem Punkt auf einem lokalen Computer bereitstellen, wird ein Eingabefeld für die IP-Adresse mit einer Schaltfläche "Verbinden" angezeigt. Wenn Sie eine IP-Adresse eingeben und auf Verbinden klicken, wird XR initialisiert und versucht, eine Verbindung mit dem Zielgerät herzustellen:

    ![Screenshot der Beispiel-App mit Beispiel-App-Remoting-Benutzeroberfläche](images/openxr-sample-app-remoting.png)

6. Um benutzerdefinierten Verbindungscode zu schreiben, rufen `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` Sie mit einem ausgefüllten `RemotingConfiguration` auf. Die Beispiel-App macht dies im Inspektor verfügbar und zeigt, wie sie die IP-Adresse aus einem Textfeld einfüllt. Durch Aufrufen von wird die Konfiguration festgelegt und XR automatisch initialisiert. Aus diesem Grund muss `Connect` XR als Coroutine aufgerufen werden:

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

7. Während der Ausführung können Sie den aktuellen Verbindungsstatus mit der API abrufen und optional XR mit trennen `AppRemoting.TryGetConnectionState` und `AppRemoting.Disconnect()` initialisieren. Dies kann verwendet werden, um die Verbindung zu trennen und innerhalb derselben App-Sitzung erneut mit einem anderen Gerät zu verbinden. Die Beispiel-App stellt einen umsetzbaren Cube zur Auswahl, mit dem die Remotingsitzung getrennt wird, wenn sie angeknippt wird.

### <a name="migration-from-previous-apis"></a>Migration von vorherigen APIs

#### <a name="unityenginexrwsaholographicremoting"></a>UnityEngine.XR.WSA.HolographicRemoting

Aus dem Beispielcode in [der Unity-Dokumentation:](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html)

| Xr. WSA. HolographicRemoting | OpenXR.Remoting.AppRemoting |
| ---- | ---- |
| `HolographicRemoting.Connect(String)` | `AppRemoting.Connect(RemotingConfiguration)` |
| `HolographicRemoting.ConnectionState` | `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `StartCoroutine(LoadDevice("WindowsMR"))`| [N/A: Automatisch beim Aufrufen von `AppRemoting.Connect` ]  |

#### <a name="unityenginexrwindowsmrwindowsmrremoting"></a>UnityEngine.XR.WindowsMR.WindowsMRRemoting

| Xr. WindowsMR.WindowsMRRemoting | OpenXR.Remoting.AppRemoting |
| ---- | ---- |
| `WindowsMRRemoting.Connect()` | `AppRemoting.Connect(RemotingConfiguration)` |
| `WindowsMRRemoting.Disconnect()` | `AppRemoting.Disconnect()` |
| `WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` und `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`| `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName` | Übergeben an `AppRemoting.Connect` über die `RemotingConfiguration` -Struktur |
| `WindowsMRRemoting.isConnected` | `AppRemoting.TryGetConnectionState(out ConnectionState state, out _) && state == ConnectionState.Connected`