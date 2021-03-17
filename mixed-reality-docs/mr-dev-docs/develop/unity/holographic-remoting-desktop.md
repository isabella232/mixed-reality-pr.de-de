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
# <a name="holographic-remoting-in-desktop-app"></a>Holographic Remoting in der Desktop-App

> [!NOTE]
> Remoting-Unterstützung für eigenständige Windows-Apps wurde in der 0.1.3-Paketversion hinzugefügt
> Ab Version 0.1.3 unterstützt diese Funktion keine UWP-Builds.

1. Befolgen Sie die Schritte in [Holographic Remoting-Setup](openxr-supported-features.md#holographic-remoting-setup) .
2. Öffnen Sie die **Projekteinstellungen für die > bearbeiten**, navigieren Sie zu der **XR-Plug-in-Verwaltung**, und aktivieren Sie das Kontrollkästchen **Windows Mixed Reality Feature Set** . Deaktivieren Sie außerdem die Option " **XR beim Start initialisieren**":

    ![Screenshot des Bereichs "Projekteinstellungen" im Unity-Editor geöffnet, bei dem "XR beim Start initialisieren" deaktiviert ist](images/openxr-features-img-02-app.png)

3. Erweitern Sie unter **openxr** den Abschnitt **Features** , und wählen Sie **Alle anzeigen** aus.
4. Aktivieren Sie das Kontrollkästchen " **Holographic App Remoting** ":

    ![Screenshot des Bereichs "Projekteinstellungen" im Unity-Editor mit aktiviertem App-Remoting](images/openxr-features-img-03-app.png)

5. Als nächstes schreiben Sie Code, um die Remotingkonfiguration und die Initialisierung von "XR Die mit dem [Mixed Reality openxr-Plug](openxr-getting-started.md#hololens-2-samples) -in verteilte Beispiel-app enthält AppRemoting.cs, das ein Beispielszenario für das Herstellen einer Verbindung mit einer bestimmten IP-Adresse zur Laufzeit anzeigt. Wenn Sie die Beispiel-APP an diesem Punkt auf einem lokalen Computer bereitstellen, wird ein Eingabefeld für die IP-Adresse mit der Schaltfläche Verbinden angezeigt. Wenn Sie eine IP-Adresse eingeben und auf Verbinden klicken, wird XR initialisiert, und es wird versucht, eine Verbindung zum Zielgerät herzustellen

    ![Screenshot der Beispiel-App mit Beispiel-App-Remoting-Benutzeroberfläche](images/openxr-sample-app-remoting.png)

6. Um benutzerdefinierten Verbindungs Code zu schreiben, müssen Sie `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` mit einem ausgefüllten-Befehl aufzurufen `RemotingConfiguration` . Die Beispiel-App macht dies im Inspektor verfügbar und zeigt, wie die IP-Adresse aus einem Textfeld ausgefüllt wird. Durch Aufrufen von `Connect` wird die Konfiguration festgelegt, und der XR wird automatisch initialisiert, weshalb Sie als Coroutine aufgerufen werden muss:

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

7. Während der Ausführung können Sie den aktuellen Verbindungsstatus mit der API abrufen und optional die Verbindung mit dem `AppRemoting.TryGetConnectionState` XR trennen und die Initialisierung mithilfe von aufheben `AppRemoting.Disconnect()` . Diese kann verwendet werden, um die Verbindung zu einem anderen Gerät innerhalb derselben App-Sitzung zu trennen und erneut eine Verbindung herzustellen. Die Beispiel-App bietet einen zu fügbaren Cube, der die Remote Sitzung trennt, wenn Sie getippt wird.

### <a name="migration-from-previous-apis"></a>Migration von vorherigen APIs

#### <a name="unityenginexrwsaholographicremoting"></a>Unityengine. XR. WSA. holographikremoting

Aus dem Beispielcode für die [Unity-](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html)Dokumentation:

| XR. WSA. Holographikremoting | Openxr. Remoting. appremoting |
| ---- | ---- |
| `HolographicRemoting.Connect(String)` | `AppRemoting.Connect(RemotingConfiguration)` |
| `HolographicRemoting.ConnectionState` | `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `StartCoroutine(LoadDevice("WindowsMR"))`| [N/v: automatisch beim Aufrufen von `AppRemoting.Connect` ]  |

#### <a name="unityenginexrwindowsmrwindowsmrremoting"></a>Unityengine. XR. windowsmr. windowsmrremoting

| XR. Windowsmr. windowsmrremoting | Openxr. Remoting. appremoting |
| ---- | ---- |
| `WindowsMRRemoting.Connect()` | `AppRemoting.Connect(RemotingConfiguration)` |
| `WindowsMRRemoting.Disconnect()` | `AppRemoting.Disconnect()` |
| `WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` und `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`| `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName` | An `AppRemoting.Connect` über die Struktur übermittelt `RemotingConfiguration` |
| `WindowsMRRemoting.isConnected` | `AppRemoting.TryGetConnectionState(out ConnectionState state, out _) && state == ConnectionState.Connected`