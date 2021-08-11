---
title: Holographic Remoting in Unity
description: Erfahren Sie, wie Sie Holographic Remoting in einer Desktop-App und im Unity Play-Modus mit OpenXR verwenden.
author: hferrone
ms.author: v-vtieto
ms.date: 07/26/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, Augmented Reality, Virtual Reality, Mixed Reality-Headsets, Learn, Tutorial, Erste Schritte, holografisches Remoting, Desktop
ms.openlocfilehash: 0b18bf4a187190da3ef9d17fd87f2c42feaa271210345330887ce618b49a0442
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115192190"
---
# <a name="holographic-remoting-in-unity"></a>Holographic Remoting in Unity

> [!NOTE]
> Windows Die Remotingunterstützung für eigenständige Apps wurde in der Paketversion 0.1.3 hinzugefügt.
> Ab Version 0.1.3 unterstützt dieses Feature keine UWP-Builds.

[Erlernen der Grundlagen von Holographic Remoting.](../platform-capabilities-and-apis/holographic-remoting-overview.md)

Sie können Holographic Remoting verwenden, um holografische Inhalte in Echtzeit an Ihre HoloLens 2 zu streamen. Dies ist eine hervorragende Möglichkeit, Ihre App schnell zu debuggen, ohne ein vollständiges Projekt zu erstellen und bereitzustellen. 

Bevor Sie beginnen, ist es wichtig, ihre beiden Hauptoptionen in Unity zu verstehen:
* **Holographic Remoting im Unity Play-Modus:** Führen Sie Ihre App lokal im Unity-Editor auf Ihrem PC im Wiedergabemodus aus, um eine schnelle Möglichkeit zum Anzeigen einer Vorschau Ihrer Inhalte auf einem HoloLens 2 bereitzustellen. Der Wiedergabemodus kann auch mit einem Windows Mixed Reality Headset verwendet werden, das an Ihren Entwicklungs-PC angefügt ist.
* **Holographic Remoting aus einer Unity-Builddatei:** Führen Sie Ihre App aus einer Unity Holographic Remoting-Remoteanwendung aus, die Sie auf Ihren Desktop in Ihren HoloLens 2 exportiert haben. Dies kann hilfreich sein, wenn Ihre App über Objekte oder Modelle mit hoher Auflösung verfügt. Ihre Desktop-GPU verarbeitet das Rendering, bevor es zum HoloLens 2 gelangt.

## <a name="holographic-remoting-setup"></a>Holographic Remoting-Setup

Unabhängig davon, welche Route Sie mit Holographic Remoting verwenden, müssen Sie [die Holographic Remoting Player-App](https://www.microsoft.com/store/productId/9NBLGGH4SV40) über die Microsoft Store auf Ihrem HoloLens 2 installieren.

Führen Sie nach dem Herunterladen die Holographic Remoting Player-App auf Ihrem HoloLens 2 aus, und Sie sehen die Versionsnummer und DIE IP-Adresse, mit der eine Verbindung hergestellt werden soll. **Sie benötigen v2.4 oder höher, um mit dem OpenXR-Plug-In zu arbeiten.**

![Screenshot des holografischen Remoting-Players, der im HoloLens](images/openxr-features-img-01.png)

## <a name="unity-play-mode-with-holographic-remoting"></a>Unity-Wiedergabemodus mit Holographic Remoting

[!INCLUDE[](includes/unity-play-mode.md)]

Holographic Remoting erfordert einen schnellen PC und Wi-Fi Verbindung. Weitere Informationen finden Sie in der [Holographic Remoting](../platform-capabilities-and-apis/holographic-remoting-player.md) Player-Dokumentation.

Um optimale Ergebnisse zu erzielen, stellen Sie sicher, dass Ihre App den [Fokuspunkt](focus-point-in-unity.md)ordnungsgemäß festlegt. Dies hilft Holographic Remoting dabei, Ihre Szene an die Latenz Ihrer Funkverbindung anzupassen.

## <a name="holographic-remoting-from-a-remote-application"></a>Holographic Remoting aus einer Remoteanwendung

1. Wählen Sie in der Menüleiste **bearbeiten > Project Einstellungen** aus.
1. Wählen Sie in der linken Spalte **XR-Plug-In-Verwaltung** aus.
1. Wählen Sie im Abschnitt **XR-Plug-In-Verwaltung** **Microsoft HoloLens Featuregruppe** und **Holographic Remoting-Remote-App-Featuregruppe** aus.
1. Deaktivieren Sie **XR beim Start initialisieren:**

    ![Screenshot: Geöffneter Bereich "Projekteinstellungen" im Unity-Editor mit deaktivierter Option "XR beim Start initialisieren"](images/001-openxr-features.png)

1. Schreiben Sie Code, um die Remotingkonfiguration festzulegen und die XR-Initialisierung auszulösen. Die mit dem [Mixed Reality OpenXR-Plug-In](./xr-project-setup.md#unity-sample-projects-for-openxr-and-hololens-2) verteilte Beispiel-App enthält AppRemoting.cs, die ein Beispielszenario zum Herstellen einer Verbindung mit einer bestimmten IP-Adresse zur Laufzeit zeigt. Wenn Sie die Beispiel-App an diesem Punkt auf einem lokalen Computer bereitstellen, wird ein Eingabefeld für die IP-Adresse mit einer Verbindungsschaltfläche angezeigt. Wenn Sie eine IP-Adresse eingeben und auf Verbinden klicken, wird XR initialisiert und versucht, eine Verbindung mit dem Zielgerät herzustellen:

    ![Screenshot der Beispiel-App mit Beispiel-App-Remoting-Benutzeroberfläche](images/openxr-sample-app-remoting.png)

1. Um benutzerdefinierten Verbindungscode zu schreiben, rufen Sie `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` mit einem ausgefüllten `RemotingConfiguration` auf. Die Beispiel-App macht dies im Inspektor verfügbar und zeigt, wie die IP-Adresse aus einem Textfeld ausgefüllt wird. Wenn Sie `Connect` aufrufen, wird die Konfiguration festgelegt und XR automatisch initialisiert. Daher muss sie als Coroutine aufgerufen werden:

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

1. Während der Ausführung können Sie den aktuellen Verbindungsstatus mit der API abrufen `AppRemoting.TryGetConnectionState` und XR optional trennen und die Initialisierung mithilfe von `AppRemoting.Disconnect()` deaktivieren. Dies kann verwendet werden, um die Verbindung mit einem anderen Gerät innerhalb derselben App-Sitzung zu trennen und erneut herzustellen. Die Beispiel-App stellt einen Cube bereit, der die Remotingsitzung trennt, wenn darauf getippt wird.

### <a name="migration-from-previous-apis"></a>Migration von vorherigen APIs

#### <a name="unityenginexrwsaholographicremoting"></a>UnityEngine.XR.WSA.HolographicRemoting

Aus dem Beispielcode in [der Unity-Dokumentation:](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html)

| Xr. WSA. HolographicRemoting | OpenXR.Remoting.AppRemoting |
| ---- | ---- |
| `HolographicRemoting.Connect(String)` | `AppRemoting.Connect(RemotingConfiguration)` |
| `HolographicRemoting.ConnectionState` | `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `StartCoroutine(LoadDevice("WindowsMR"))`| [N/A: Wird automatisch beim Aufrufen von `AppRemoting.Connect` ]  |

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
* [Tutorial: Erste Schritte mit PC Holographic Remoting](../unity/tutorials/mr-learning-pc-holographic-remoting-01.md)
* [Tutorial: Erstellen einer Holographic Remoting-PC-Anwendung](../unity/tutorials/mr-learning-pc-holographic-remoting-02.md)
