---
title: Schreiben einer Holographic Remoting-Remote-app (openxr)
description: Durch das Erstellen einer Holographic Remoting Remote-app, die auf einem Remote Computer gerendert wird, kann auf hololens 2 gestreamt werden. In diesem Artikel wird beschrieben, wie dies erreicht werden kann.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: Hololens, Remoting, Holographic Remoting, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, nuget
ms.openlocfilehash: 7e46c67e7dac08759890fa66d540379991414aad
ms.sourcegitcommit: 9664bcc10ed7e60f7593f3a7ae58c66060802ab1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/01/2020
ms.locfileid: "96469503"
---
# <a name="writing-a-holographic-remoting-remote-app-using-the-openxr-api"></a>Schreiben einer Holographic Remoting-Remote-App mithilfe der openxr-API

>[!IMPORTANT]
>In diesem Dokument wird die Erstellung einer Remote Anwendung für hololens 2-und Windows Mixed Reality-Headsets mithilfe der [openxr-API](../native/openxr.md)beschrieben. Für Remote Anwendungen für **hololens (1st Gen)** muss das nuget-Paketversion **1. x. x** verwendet werden. Dies bedeutet, dass für hololens 2 geschriebene Remote Anwendungen nicht mit hololens 1 und umgekehrt kompatibel sind. Die Dokumentation für hololens 1 finden Sie [hier](add-holographic-remoting.md).

Wenn Sie eine Holographic Remoting-Remote-app erstellen, können Remote Inhalte, die auf einem Remote Computer gerendert werden, an hololens 2 und immersive Geräte wie Windows Mixed Reality-Headsets gestreamt werden. In diesem Artikel wird beschrieben, wie dies erreicht werden kann. Sämtlicher Code auf dieser Seite und in den Arbeitsprojekten finden Sie im [GitHub-Repository "Holographic Remoting Samples](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)".

Holographic Remoting ermöglicht einer APP das Ausrichten von hololens 2-und Windows Mixed Reality-Headsets mit Holographic-Inhalten, die auf einem Desktop-PC oder auf einem UWP-Gerät wie der Xbox One gerendert werden, und ermöglicht so den Zugriff auf mehr Systemressourcen und ermöglicht die Integration von Remote- [immersiven Ansichten](../../design/app-views.md) in vorhandene Desktop-PCs. Eine Remote-app empfängt einen Eingabedaten Strom von hololens 2, rendert Inhalte in einer virtuellen immersiven Ansicht und streamt Inhalts Frames zurück an hololens 2. Die Verbindung wird mithilfe von Standard-Wi-Fi hergestellt. Holographic-Remoting wird mithilfe eines nuget-Pakets zu einer Desktop-oder UWP-app hinzugefügt. Zusätzlicher Code ist erforderlich, der die Verbindung verarbeitet und in einer immersiven Ansicht rendert.

Eine typische remotingverbindung verfügt über bis zu 50 ms Latenzzeit. Die Player-App kann die Latenzzeit in Echtzeit melden.

## <a name="prerequisites"></a>Voraussetzungen

Ein guter Ausgangspunkt ist eine funktionierende openxr-basierte Desktop-oder UWP-app. Weitere Informationen finden Sie [unter Getting Started with openxr](../native/openxr-getting-started.md).

>[!IMPORTANT]
>Jede APP, die Holographic Remoting verwendet, sollte für die Verwendung eines [Multithread-Apartment](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments)erstellt werden. Die Verwendung eines [Single Thread-Apartment](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) wird unterstützt, führt jedoch zu einer nicht optimalen Leistung und kann während der Wiedergabe möglicherweise zu einem stutor werden. Bei Verwendung von C++/WinRT [WinRT:: init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) ist ein Multithread-Apartment der Standard.

## <a name="get-the-holographic-remoting-nuget-package"></a>Holen Sie sich das Holographic Remoting-nuget-Paket.

Die folgenden Schritte sind erforderlich, um das nuget-Paket einem Projekt in Visual Studio hinzuzufügen.
1. Öffnen Sie das Projekt in Visual Studio.
2. Klicken Sie mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie **nuget-Pakete verwalten aus.**
3. Klicken Sie im angezeigten Bereich auf **Durchsuchen** , und suchen Sie nach "Holographic Remoting".
4. Wählen Sie **Microsoft. Holographic. Remoting. openxr** aus, stellen Sie sicher, dass die neueste Version **2. x. x** ausgewählt ist, und klicken Sie auf **Installieren**.
5. Wenn das Dialogfeld **Vorschau** angezeigt wird, klicken Sie auf **OK**.
6. Das nächste Dialogfeld, das angezeigt wird, ist die Lizenzvereinbarung. Klicken Sie auf **ich** Stimme zu, um den Lizenzvertrag zu akzeptieren.
7. Wiederholen Sie die Schritte 3 bis 6 für die folgenden nuget-Pakete: openxr. Headers, openxr. Loader

>[!NOTE]
>Version **1. x. x** des nuget-Pakets ist weiterhin für Entwickler verfügbar, die auf hololens 1 abzielen möchten. Weitere Informationen finden [Sie unter Hinzufügen von Holographic Remoting (hololens (1st Gen))](add-holographic-remoting.md).

## <a name="select-the-holographic-remoting-openxr-runtime"></a>Wählen Sie das Holographic-Remoting openxr Runtime aus.

Der erste Schritt, den Sie in Ihrer Remote-app ausführen müssen, ist die Auswahl der Holographic-Remoting-openxr-Laufzeit, die Teil des nuget-Pakets Microsoft. Holographic. Remoting. openxr ist. Hierfür können Sie die ```XR_RUNTIME_JSON``` Umgebungsvariable auf den Pfad der RemotingXR.jsDatei in der APP festlegen. Diese Umgebungsvariable wird vom openxr-Loader verwendet, um die System Standard-openxr-Laufzeit nicht zu verwenden, sondern zur "Holographic Remoting openxr Runtime" umzuleiten. Wenn Sie das nuget-Paket Microsoft. Holographic. Remoting. openxr verwenden, wird der RemotingXR.jsfür die Datei während der Kompilierung automatisch in den Ausgabeordner kopiert. Daher sieht die openxr-Lauf Zeitauswahl in der Regel wie folgt aus.

```cpp
bool EnableRemotingXR() {
    wchar_t executablePath[MAX_PATH];
    if (GetModuleFileNameW(NULL, executablePath, ARRAYSIZE(executablePath)) == 0) {
        return false;
    }
    
    std::filesystem::path filename(executablePath);
    filename = filename.replace_filename("RemotingXR.json");

    if (std::filesystem::exists(filename)) {
        SetEnvironmentVariableW(L"XR_RUNTIME_JSON", filename.c_str());
            return true;
        }

    return false;
}
```

## <a name="create-xrinstance-with-holographic-remoting-extension"></a>Erstellen einer xrinstance mit Holographic Remoting-Erweiterung

Der erste Schritt, den eine typische openxr-app ausführen soll, besteht darin, openxr-Erweiterungen auszuwählen und eine xrinstance-Instanz zu erstellen. Die openxr Core-Spezifikation bietet keine Remoting-spezifische API. Aus diesem Grund führt Holographic Remoting die eigene openxr-Erweiterung namens ein ```XR_MSFT_holographic_remoting``` . Stellen Sie sicher, dass beim Aufrufen von xrkreateinstance der ```XR_MSFT_HOLOGRAPHIC_REMOTING_EXTENSION_NAME``` in xrinstancecreateinfo enthalten ist.

>[!TIP]
>Standardmäßig wird der gerenderte Inhalt Ihrer app nur an den Holographic Remoting-Player gestreamt, der entweder auf einem hololens 2 oder auf einem Windows Mixed Reality-Headsets ausgeführt wird. Um den gerenderten Inhalt auf dem Remote-PC auch über eine SwapChain eines Fensters anzuzeigen, bietet Holographic Remoting eine zweite openxr-Erweiterung mit dem Namen ```XR_MSFT_holographic_remoting_frame_mirroring``` . Stellen Sie sicher, dass diese Extension auch mit aktivieren, ```XR_MSFT_HOLOGRAPHIC_REMOTING_FRAME_MIRRORING_EXTENSION_NAME``` Falls Sie diese Funktion verwenden möchten.

>[!IMPORTANT]
>Weitere Informationen zur API für die Holographic Remoting openxr-Erweiterung finden Sie in der [Spezifikation](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html) , die im [GitHub-Repository "Holographic Remoting Samples](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)" zu finden ist.

## <a name="connect-to-the-device"></a>Verbindung mit dem Gerät herstellen

Nachdem Ihre Remote-app die xrinstance erstellt und die xrsystemid über xrgetsystem abgefragt hat, kann eine Verbindung mit dem Player Gerät hergestellt werden.

>[!WARNING]
> Das Holographic-Remoting openxr Runtime kann nur gerätespezifische Daten bereitstellen, z. b. Ansichts Konfigurationen oder Umgebungs Blend-Modi, nachdem eine Verbindung hergestellt wurde. ```xrEnumerateViewConfigurations```, ```xrEnumerateViewConfigurationViews``` , ```xrGetViewConfigurationProperties``` , ```xrEnumerateEnvironmentBlendModes``` und verfügen ```xrGetSystemProperties``` über Standardwerte, die Sie in der Regel erhalten, wenn Sie eine Verbindung mit einem Player herstellen, der auf einem hololens 2 ausgeführt wird, bevor eine vollständige Verbindung hergestellt wird.
Es wird dringend empfohlen, diese Methoden nicht aufzurufen, bevor eine Verbindung hergestellt wurde. Der Vorschlag ist die Verwendung dieser Methoden, nachdem die xrsession erfolgreich erstellt wurde und der Sitzungszustand mindestens XR_SESSION_STATE_READY ist.

Allgemeine Eigenschaften wie z. b. Max. Bitrate, audiofähig, Videocodec oder tiefe Puffer Datenstrom Auflösung können ```xrRemotingSetContextPropertiesMSFT``` wie folgt konfiguriert werden.

```cpp
XrRemotingRemoteContextPropertiesMSFT contextProperties;
contextProperties = XrRemotingRemoteContextPropertiesMSFT{static_cast<XrStructureType>(XR_TYPE_REMOTING_REMOTE_CONTEXT_PROPERTIES_MSFT)};
contextProperties.enableAudio = false;
contextProperties.maxBitrateKbps = 20000;
contextProperties.videoCodec = XR_REMOTING_VIDEO_CODEC_H265_MSFT;
contextProperties.depthBufferStreamResolution = XR_REMOTING_DEPTH_BUFFER_STREAM_RESOLUTION_HALF_MSFT;
xrRemotingSetContextPropertiesMSFT(m_instance.Get(), m_systemId, &contextProperties);
```

Die Verbindung kann auf zwei Arten erreicht werden.
1) Die Remote-app stellt eine Verbindung zum Player her, der auf dem Gerät ausgeführt wird.
2) Der Player, der auf dem Gerät ausgeführt wird, stellt eine Verbindung zur Remote-app her

Um eine Verbindung zwischen der Remote-app und dem Player-Gerät herzustellen, geben Sie die-Methode an, die ```xrRemotingConnectMSFT``` den Hostnamen und den Port über die  ```XrRemotingConnectInfoMSFT``` Struktur angibt. Der von Holographic Remoting Player verwendete Port ist **8265**.

```cpp
XrRemotingConnectInfoMSFT connectInfo{static_cast<XrStructureType>(XR_TYPE_REMOTING_CONNECT_INFO_MSFT)};
connectInfo.remoteHostName = "192.168.x.x";
connectInfo.remotePort = 8265;
connectInfo.secureConnection = false;
xrRemotingConnectMSFT(m_instance.Get(), m_systemId, &connectInfo);
```

Das Lauschen auf eingehende Verbindungen in der Remote-app kann durch Aufrufen der- ```xrRemotingListenMSFT``` Methode erfolgen. Der Handshake-und der transportport können über die-Struktur angegeben werden ```XrRemotingListenInfoMSFT``` . Der Handshake-Port wird für den ersten Handshake verwendet. Die Daten werden dann über den transportport gesendet. Standardmäßig werden **8265** und **8266** verwendet.

```cpp
XrRemotingListenInfoMSFT listenInfo{static_cast<XrStructureType>(XR_TYPE_REMOTING_LISTEN_INFO_MSFT)};
listenInfo.listenInterface = "0.0.0.0";
listenInfo.handshakeListenPort = 8265;
listenInfo.transportListenPort = 8266;
listenInfo.secureConnection = false;
xrRemotingListenMSFT(m_instance.Get(), m_systemId, &listenInfo);
```

Der Verbindungsstatus muss getrennt werden, wenn Sie ```xrRemotingConnectMSFT``` oder aufruft ```xrRemotingListenMSFT``` . Der Verbindungsstatus kann jederzeit abgerufen werden, nachdem Sie eine xrinstance erstellt und für die xrsystemid mithilfe von abgefragt haben ```xrRemotingGetConnectionStateMSFT``` .

```cpp
XrRemotingConnectionStateMSFT connectionState;
xrRemotingGetConnectionStateMSFT(m_instance.Get(), m_systemId, &connectionState, nullptr);
```

Folgende Verbindungszustände sind verfügbar:
- XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT
- XR_REMOTING_CONNECTION_STATE_CONNECTING_MSFT
- XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT

>[!IMPORTANT]
> ```xrRemotingConnectMSFT``` oder ```xrRemotingListenMSFT``` muss aufgerufen werden, bevor versucht wird, eine xrsession über xrkreatesession zu erstellen. Wenn Sie versuchen, eine xrsession-Sitzung zu erstellen, während der Verbindungsstatus ist, ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` wird die Sitzungs Erstellung erfolgreich ausgeführt, aber der Sitzungszustand wird sofort in XR_SESSION_STATE_LOSS_PENDING übergehen.

Die Implementierung von Holographic Remoting ```xrCreateSession``` unterstützt das warten auf das Herstellen einer Verbindung. Sie können einen-Aufrufvorgang ```xrRemotingConnectMSFT``` oder ```xrRemotingListenMSFT``` direkt gefolgt von einem-Befehl durchlaufen ```xrCreateSession``` , der blockiert und darauf wartet, dass eine Verbindung hergestellt wird. Das Timeout ist auf 10 Sekunden korrigiert. Wenn innerhalb dieses Zeitraums eine Verbindung hergestellt werden kann, wird die xrsession-Erstellung erfolgreich ausgeführt, und der Sitzungs Status wechselt zu XR_SESSION_STATE_READY. Für den Fall, dass keine Verbindung hergestellt werden kann, ist auch die Sitzungs Erstellung erfolgreich, aber es erfolgt sofort zu XR_SESSION_STATE_LOSS_PENDING.

Im Allgemeinen ist der Verbindungsstatus ein paar mit dem xrsession-Zustand. Jede Änderung des Verbindungsstatus wirkt sich auch auf den Sitzungs Status aus. Wenn beispielsweise der Verbindungsstatus von `XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT` in ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` den Sitzungs Status wechselt, wechselt ebenfalls zu XR_SESSION_STATE_LOSS_PENDING.

## <a name="handling-remoting-specific-events"></a>Behandeln von Remoting-spezifischen Ereignissen

Das Holographic-Remoting openxr Runtime macht drei Ereignisse verfügbar, die für die Überwachung des Zustands einer Verbindung wichtig sind.
1) ```XR_TYPE_REMOTING_EVENT_DATA_CONNECTED_MSFT```: Wird ausgelöst, wenn eine Verbindung mit dem Gerät erfolgreich hergestellt wurde.
2) ```XR_TYPE_REMOTING_EVENT_DATA_DISCONNECTED_MSFT```: Wird ausgelöst, wenn eine etablierte Verbindung geschlossen wird oder keine Verbindung hergestellt werden konnte.
3) ```XR_TYPE_REMOTING_EVENT_DATA_LISTENING_MSFT```: Beim lauschen auf eingehende Verbindungen wird gestartet.

Diese Ereignisse werden in einer Warteschlange platziert, und Ihre Remote-app muss mit Regularität über die Warteschlange lesen ```xrPollEvent``` .

```cpp
auto pollEvent = [&](XrEventDataBuffer& eventData) -> bool {
    eventData.type = XR_TYPE_EVENT_DATA_BUFFER;
    eventData.next = nullptr;
    return CHECK_XRCMD(xrPollEvent(m_instance.Get(), &eventData)) == XR_SUCCESS;
};

XrEventDataBuffer eventData{};
while (pollEvent(eventData)) {
    switch (eventData.type) {
    
    ...
    
    case XR_TYPE_REMOTING_EVENT_DATA_LISTENING_MSFT: {
        DEBUG_PRINT("Holographic Remoting: Listening on port %d",
                    reinterpret_cast<const XrRemotingEventDataListeningMSFT*>(&eventData)->listeningPort);
        break;
    }
    case XR_TYPE_REMOTING_EVENT_DATA_CONNECTED_MSFT: {
        DEBUG_PRINT("Holographic Remoting: Connected.");
        break;
    }
    case XR_TYPE_REMOTING_EVENT_DATA_DISCONNECTED_MSFT: {
        DEBUG_PRINT("Holographic Remoting: Disconnected - Reason: %d",
                    reinterpret_cast<const XrRemotingEventDataDisconnectedMSFT*>(&eventData)->disconnectReason);
        break;
    }
}
```

## <a name="preview-streamed-content-locally"></a>Vorschau der lokal gestreuten Inhalte

Zum Anzeigen desselben Inhalts in der Remote-app, die an das Gerät gesendet wird, ```XR_MSFT_holographic_remoting_frame_mirroring``` kann die Erweiterung verwendet werden. Mit dieser Erweiterung können Sie eine Textur an den xrendframe übermitteln. Dies erfolgt mithilfe der- ```XrRemotingFrameMirrorImageInfoMSFT``` Struktur, die wie folgt mit xrframedinfo verkettet ist.

```cpp
XrFrameEndInfo frameEndInfo{XR_TYPE_FRAME_END_INFO};
...

XrRemotingFrameMirrorImageD3D11MSFT mirrorImageD3D11{
    static_cast<XrStructureType>(XR_TYPE_REMOTING_FRAME_MIRROR_IMAGE_D3D11_MSFT)};
mirrorImageD3D11.texture = m_window->GetNextSwapchainTexture();

XrRemotingFrameMirrorImageInfoMSFT mirrorImageEndInfo{
    static_cast<XrStructureType>(XR_TYPE_REMOTING_FRAME_MIRROR_IMAGE_INFO_MSFT)};
mirrorImageEndInfo.image = reinterpret_cast<const XrRemotingFrameMirrorImageBaseHeaderMSFT*>(&mirrorImageD3D11);

frameEndInfo.next = &mirrorImageEndInfo;

xrEndFrame(m_session.Get(), &frameEndInfo);

m_window->PresentSwapchain();
```

Im obigen Beispiel wird eine DX11-Swap-Chain-Textur verwendet, und das Fenster wird unmittelbar nach dem xrendframe-Rückruf dargestellt. Die Verwendung ist nicht auf die Texturen der Austausch Kette beschränkt, und es ist keine zusätzliche GPU-Synchronisierung erforderlich. Ausführliche Informationen zur Verwendung und zu Einschränkungen finden Sie in der [Erweiterungs Spezifikation](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html#XR_MSFT_remoting_frame_mirroring).
Wenn Ihre Remote-app DX12 verwendet, verwenden Sie XrRemotingFrameMirrorImageD3D12MSFT anstelle von XrRemotingFrameMirrorImageD3D11MSFT.

## <a name="see-also"></a>Weitere Informationen
* [Schreiben einer benutzerdefinierten Holographic Remoting Player-App](holographic-remoting-create-player.md)
* [Einrichten einer sicheren Verbindung mit Holographic Remoting](holographic-remoting-secure-connection.md)
* [Problembehandlung und Einschränkungen für Holographic Remoting](holographic-remoting-troubleshooting.md)
* [Holographic Remoting-Software – Lizenzbedingungen](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Datenschutzerklärung von Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)
