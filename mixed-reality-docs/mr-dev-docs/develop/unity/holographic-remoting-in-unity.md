---
title: Holographic Remoting in Unity
description: Erfahren Sie, wie Sie Holographic Remoting in einer Desktop-App und im Unity Play-Modus mit OpenXR verwenden.
author: hferrone
ms.author: v-vtieto
ms.date: 07/26/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, Augmented Reality, Virtual Reality, Mixed Reality-Headsets, Lernen, Tutorial, Erste Schritte, holografisches Remoting, Desktop
ms.openlocfilehash: 51244a94fb7e54f2eee41d9d1b7f65b0ba373138
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757424"
---
# <a name="holographic-remoting-in-unity"></a>Holographic Remoting in Unity

> [!NOTE]
> Windows Unterstützung für eigenständiges App-Remoting wurde in der Paketversion 0.1.3 hinzugefügt.
> Ab Version 0.1.3 unterstützt dieses Feature keine UWP-Builds.

[Lernen Sie die Grundlagen von Holographic Remoting.](../platform-capabilities-and-apis/holographic-remoting-overview.md)

Sie können Holographic Remoting verwenden, um holografische Inhalte in Echtzeit an HoloLens 2 Daten zu streamen. Dies ist eine hervorragende Möglichkeit, Ihre App schnell zu debuggen, ohne ein vollständiges Projekt zu erstellen und bereitzustellen. 

Bevor Sie beginnen, ist es wichtig, Ihre beiden Hauptoptionen in Unity zu verstehen:
* **Holographic Remoting im Unity** Play-Modus: Führen Sie Ihre App lokal im Unity-Editor auf Ihrem PC im Wiedergabemodus aus, um eine schnelle Möglichkeit zum Anzeigen einer Vorschau Ihrer Inhalte auf einer HoloLens 2. Der Wiedergabemodus kann auch mit einem Windows Mixed Reality Headset verwendet werden, das an Ihren Entwicklungs-PC angeschlossen ist.
* **Holographic Remoting aus** einer Unity-Builddatei: Führen Sie Ihre App aus einer Unity Holographic Remoting-Remoteanwendung aus, die Sie auf Ihren Desktop in Ihre HoloLens 2. Dies kann hilfreich sein, wenn Ihre App über hochauflösungsbasierte Ressourcen oder Modelle verfügt. Ihre Desktop-GPU verarbeitet das Rendering, bevor es zum HoloLens 2.

## <a name="holographic-remoting-setup"></a>Holographic Remoting-Setup

Unabhängig davon, welche Route Sie mit Holographic Remoting verwenden, müssen Sie die [Holographic Remoting Player-App](https://www.microsoft.com/store/productId/9NBLGGH4SV40) aus dem Microsoft Store auf Ihrer HoloLens 2.

Nachdem sie heruntergeladen wurde, führen Sie die Holographic Remoting Player-App auf Ihrem HoloLens 2 aus, und Sie sehen die Versionsnummer und ip-Adresse, mit der eine Verbindung hergestellt werden soll. **Sie benötigen Version 2.4 oder höher, um mit dem OpenXR-Plug-In arbeiten zu können.**

![Screenshot des Holographic Remoting-Players, der in der HoloLens](images/openxr-features-img-01.png)

## <a name="unity-play-mode-with-holographic-remoting"></a>Unity-Wiedergabemodus mit Holographic Remoting

[!INCLUDE[](includes/unity-play-mode.md)]

Holographic Remoting erfordert einen schnellen PC und eine Wi-Fi Verbindung. Weitere Informationen finden Sie in der [Dokumentation zu Holographic Remoting Player.](../platform-capabilities-and-apis/holographic-remoting-player.md)

Um optimale Ergebnisse zu erzielen, stellen Sie sicher, dass Ihre App den [Fokuspunkt ordnungsgemäß fest legt.](focus-point-in-unity.md) Dies hilft Holographic Remoting dabei, Ihre Szene an die Latenz Ihrer Drahtlosverbindung anzupassen.

## <a name="holographic-remoting-from-a-remote-application"></a>Holographic Remoting aus einer Remoteanwendung

1. Wählen Sie auf der Menüleiste **Bearbeiten > Project Einstellungen.**
1. Wählen Sie in der linken Spalte **XR-Plug-In-Verwaltung aus.**
1. Wählen Sie **im Abschnitt XR-Plug-In-Verwaltung** Microsoft HoloLens **Featuregruppe und** **Holographic Remoting-Remote-App-Featuregruppe aus.**
1. Deaktivieren Sie **XR beim Start initialisieren:**

    ![Screenshot des im Unity-Editor geöffneten Fensters "Projekteinstellungen" mit deaktivierter Option "XR beim Start initialisieren"](images/001-openxr-features.png)

1. Schreiben Sie Code, um die Remotingkonfiguration zu konfigurieren und die XR-Initialisierung auszulösen. Die Beispiel-App, die mit dem [Mixed Reality OpenXR-Plug-In](./xr-project-setup.md#unity-sample-projects-for-openxr-and-hololens-2) verteilt wird, enthält AppRemoting.cs. Dies zeigt ein Beispielszenario für das Herstellen einer Verbindung mit einer bestimmten IP-Adresse zur Laufzeit. Wenn Sie die Beispiel-App an diesem Punkt auf einem lokalen Computer bereitstellen, wird ein Eingabefeld für die IP-Adresse mit einer Schaltfläche "Verbinden" angezeigt. Wenn Sie eine IP-Adresse eingeben und Verbinden klicken, wird XR initialisiert und versucht, eine Verbindung mit dem Zielgerät herzustellen:

    ![Screenshot der Beispiel-App mit Beispiel-App-Remoting-Benutzeroberfläche](images/openxr-sample-app-remoting.png)

1. Um benutzerdefinierten Verbindungscode zu schreiben, rufen `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` Sie mit einem ausgefüllten `RemotingConfiguration` auf. Die Beispiel-App macht dies im Inspektor verfügbar und zeigt, wie sie die IP-Adresse aus einem Textfeld einfüllt. Durch Aufrufen von wird die Konfiguration festgelegt und XR automatisch initialisiert. Aus diesem Grund muss `Connect` XR als Coroutine aufgerufen werden:

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

1. Während der Ausführung können Sie den aktuellen Verbindungsstatus mit der API abrufen und optional XR mit trennen `AppRemoting.TryGetConnectionState` und `AppRemoting.Disconnect()` initialisieren. Dies kann verwendet werden, um die Verbindung zu trennen und innerhalb derselben App-Sitzung erneut mit einem anderen Gerät zu verbinden. Die Beispiel-App stellt einen umsetzbaren Cube zur Auswahl, mit dem die Remotingsitzung getrennt wird, wenn sie angeknippt wird.

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

## <a name="see-also"></a>Siehe auch

* [Holographic Remoting-Player](../platform-capabilities-and-apis/holographic-remoting-player.md)
* [Tutorial: Erste Schritte mit holografischem PC-Remoting](../unity/tutorials/mr-learning-pc-holographic-remoting-01.md)
* [Tutorial: Erstellen einer Holographic Remoting-PC-Anwendung](../unity/tutorials/mr-learning-pc-holographic-remoting-02.md)
