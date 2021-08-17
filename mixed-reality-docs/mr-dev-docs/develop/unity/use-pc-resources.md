---
title: Verwenden von PC-Ressourcen zur Stromversorgung Ihrer App mit Holographic Remoting
description: Verwenden Sie PC-Ressourcen, anstatt sich auf die On-Board-Verarbeitungsleistung des HoloLens zu verlassen, um Ihre App mit Holographic Remoting zu bedienen.
author: vtieto
ms.author: v-vtieto
ms.date: 08/12/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, Augmented Reality, Virtual Reality, Mixed Reality-Headsets, Lernen, Tutorial, Erste Schritte, holografisches Remoting, Desktop, Vorschau, Debuggen
ms.openlocfilehash: 634e1a5e92ade79d1d9f0e7bfdd994cfdfb5866b
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2021
ms.locfileid: "122203851"
---
# <a name="use-pc-resources-to-power-your-app-with-holographic-remoting"></a>Verwenden von PC-Ressourcen zur Stromversorgung Ihrer App mit Holographic Remoting

In diesem Artikel wird der folgende Verwendungsfall für Holographic Remoting erläutert:

-  Sie möchten, dass die Ressourcen eines PCs Ihre App nutzen, anstatt sich auf die **HoloLens-On-Board-Ressourcen** zu verlassen: Sie können eine App erstellen und erstellen, die über Holographic Remoting-Funktionen verfügt. Der Benutzer sieht die App auf dem HoloLens, aber die App wird tatsächlich auf einem PC ausgeführt, wodurch die App die leistungsstärkeren Ressourcen des PCs nutzen kann. Dies kann besonders hilfreich sein, wenn Ihre App über hochauflösungsbasierte Ressourcen oder Modelle verfügt und die Bildfrequenz nicht darunter liegt. Wir nennen dies _eine Holographic Remoting-Remote-App._ Eingaben der HoloLens - Anvisierten, Gesten, Stimme und räumliche Zuordnung - werden an den PC gesendet, wo der Inhalt in einer virtuellen immersiven Ansicht gerendert wird. Die gerenderten Frames werden dann an die HoloLens.

Diese Art von Holographic Remoting ist auch für immersive Headsets Windows Mixed Reality (WMR) verfügbar. Dies kann beispielsweise nützlich sein, wenn Ihr WMR-Headset mit einem pc verbunden ist und Sie Ihre App von einem leistungsfähigeren PC auf den pc streamen möchten.

Weitere Informationen zu Holographic Remoting finden Sie unter [Übersicht über Holographic Remoting.](../platform-capabilities-and-apis/holographic-remoting-overview.md)

Beachten Sie, dass Sie Holographic Remoting auch verwenden können, wenn Sie ihre App während des Entwicklungsprozesses in der Vorschau anzeigen [und debuggen möchten.](preview-and-debug-your-app.md)

## <a name="set-up-holographic-remoting"></a>Einrichten von Holographic Remoting

Um Holographic Remoting verwenden zu können, müssen Sie die [Holographic Remoting Player-App](../platform-capabilities-and-apis/holographic-remoting-player.md) aus dem Microsoft Store auf Ihrem HoloLens 2. Wie unten erläutert, werden nach dem Herunterladen und Ausführen der App die Versionsnummer und die IP-Adresse angezeigt, mit der eine Verbindung hergestellt werden soll. **Sie benötigen Version 2.4 oder höher, um mit dem OpenXR-Plug-In arbeiten zu können.**

Holographic Remoting erfordert einen schnellen PC und Wi-Fi Verbindung. Weitere Informationen finden Sie im oben verlinkten Artikel Holographic Remoting Player.

![Screenshot des Holographic Remoting-Players, der in der HoloLens](images/openxr-features-img-01.png)

1. Wählen Sie auf der Menüleiste **Bearbeiten > Project Einstellungen.**
1. Wählen Sie in der linken Spalte **XR-Plug-In-Verwaltung aus.**
1. Wählen Sie **im Abschnitt XR-Plug-In-Verwaltung** Microsoft HoloLens **Featuregruppe und** **Holographic Remoting-Remote-App-Featuregruppe aus.**
1. Deaktivieren Sie **XR beim Start initialisieren:**

    ![Screenshot des im Unity-Editor geöffneten Fensters "Projekteinstellungen" mit deaktivierter Option "XR beim Start initialisieren"](images/001-openxr-features.png)

1. Schreiben Sie Code, um die Remotingkonfiguration zu konfigurieren und die XR-Initialisierung auszulösen. Die Beispiel-App, die mit dem [Mixed Reality OpenXR-Plug-In](./xr-project-setup.md#unity-sample-projects-for-openxr-and-hololens-2) verteilt wird, enthält AppRemoting.cs. Dies zeigt ein Beispielszenario für das Herstellen einer Verbindung mit einer bestimmten IP-Adresse zur Laufzeit. Wenn Sie die Beispiel-App an diesem Punkt auf einem lokalen Computer bereitstellen, wird ein Eingabefeld für die IP-Adresse mit einer Schaltfläche "Verbinden" angezeigt. Wenn Sie eine IP-Adresse eingeben und Verbinden klicken, wird XR initialisiert und versucht, eine Verbindung mit dem Zielgerät herzustellen:

    ![Screenshot der Beispiel-App mit Beispiel-App-Remoting-Benutzeroberfläche](images/openxr-sample-app-remoting.png)

1. Um benutzerdefinierten Verbindungscode zu schreiben, rufen `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` Sie mit einem ausgefüllten `RemotingConfiguration` auf. Die Beispiel-App macht dies im Inspektor verfügbar und zeigt, wie sie die IP-Adresse aus einem Textfeld einfüllt. Durch Aufrufen von wird die Konfiguration festgelegt und XR automatisch initialisiert. Aus diesem Grund muss es `Connect` als Coroutine aufgerufen werden:

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

1. Während der Ausführung können Sie den aktuellen Verbindungsstatus mit der API abrufen und optional XR mit trennen `AppRemoting.TryGetConnectionState` und `AppRemoting.Disconnect()` initialisieren. Dies kann verwendet werden, um die Verbindung zu trennen und innerhalb derselben App-Sitzung erneut mit einem anderen Gerät zu verbinden. Die Beispiel-App stellt einen umsetzbaren Cube zur Auswahl, der die Remotingsitzung bei Tippen trennt.

## <a name="migrate-from-previous-holographic-remoting-apis"></a>Migrieren von früheren Holographic Remoting-APIs

Weitere Informationen zu Holographic Remoting finden Sie unter [Übersicht über Holographic Remoting.](../platform-capabilities-and-apis/holographic-remoting-overview.md)

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

## <a name="see-also"></a>Weitere Informationen

* [Holographic Remoting-Player](../platform-capabilities-and-apis/holographic-remoting-player.md)
* [Vorschau und Debuggen Ihrer App mit holografischem Remoting und Wiedergabemodus](preview-and-debug-your-app.md)
* [Tutorial: Erste Schritte mit holografischem PC-Remoting](../unity/tutorials/mr-learning-pc-holographic-remoting-01.md)
* [Tutorial: Erstellen einer Holographic Remoting-PC-Anwendung](../unity/tutorials/mr-learning-pc-holographic-remoting-02.md)
