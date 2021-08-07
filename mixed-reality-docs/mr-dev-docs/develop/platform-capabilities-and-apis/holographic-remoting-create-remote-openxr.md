---
title: Schreiben einer Holographic Remoting-Remote-App (OpenXR)
description: Erfahren Sie, wie Sie remote auf einem Remotecomputer gerenderte Inhalte mit Holographic Remoting-Apps mit OpenXR an HoloLens 2 streamen.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, Remoting, Holographic Remoting, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, NuGet
ms.openlocfilehash: 6cf44bd031aec4b475d7496a999a3c7d4d40cae7cc921ff39cfe61698f3dd532
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212068"
---
# <a name="writing-a-holographic-remoting-remote-app-using-the-openxr-api"></a>Schreiben einer Holographic Remoting-Remote-App mithilfe der OpenXR-API

>[!IMPORTANT]
>In diesem Dokument wird die Erstellung einer Remoteanwendung für HoloLens 2 und Windows Mixed Reality Headsets mithilfe der [OpenXR-API](../native/openxr.md)beschrieben. Remoteanwendungen für **HoloLens (1. Generation)** müssen NuGet Paketversion **1.x.x** verwenden. Dies bedeutet, dass Remoteanwendungen, die für HoloLens 2 geschrieben wurden, nicht mit HoloLens 1 kompatibel sind und umgekehrt. Die Dokumentation für HoloLens 1 finden Sie [hier.](add-holographic-remoting.md)

Holographic Remoting-Apps können remote gerenderte Inhalte an HoloLens 2 und Windows Mixed Reality immersive Headsets streamen. Sie können auch auf weitere Systemressourcen zugreifen und [immersive Remoteansichten](../../design/app-views.md) in vorhandene Desktop-PC-Software integrieren. Eine Remote-App empfängt einen Eingabedatenstrom von HoloLens 2, rendert Inhalte in einer virtuellen immersiven Ansicht und streamt Inhaltsframes zurück an HoloLens 2. Die Verbindung wird mithilfe von Standard-WLAN hergestellt. Holographic Remoting wird einer Desktop- oder UWP-App über ein NuGet Paket hinzugefügt. Es ist zusätzlicher Code erforderlich, der die Verbindung verarbeitet und in einer immersiven Ansicht rendert. Eine typische Remotingverbindung hat eine Latenz von bis zu 50 ms. Die Player-App kann die Latenz in Echtzeit melden.

Den gesamten Code auf dieser Seite und funktionierende Projekte finden Sie im [GitHub-Repository für Holographic Remoting-Beispiele.](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)

## <a name="prerequisites"></a>Voraussetzungen

Ein guter Ausgangspunkt ist eine funktionierende OpenXR-basierte Desktop- oder UWP-App. Weitere Informationen finden Sie unter [Erste Schritte mit OpenXR.](../native/openxr-getting-started.md)

>[!IMPORTANT]
>Jede App, die Holographic Remoting verwendet, sollte so erstellt werden, dass sie ein [Multithread-Apartment](/windows/win32/com/multithreaded-apartments)verwendet. Die Verwendung eines [Singlethread-Apartments](/windows/win32/com/single-threaded-apartments) wird unterstützt, führt aber zu einer suboptimalen Leistung und möglicherweise zu einem Stubing während der Wiedergabe. Bei Verwendung von C++/WinRT [winrt::init_apartment](/windows/uwp/cpp-and-winrt-apis/get-started) ist ein Multithread-Apartment die Standardeinstellung.

## <a name="get-the-holographic-remoting-nuget-package"></a>Abrufen des Holographic Remoting NuGet-Pakets

Die folgenden Schritte sind erforderlich, um das NuGet-Paket einem Projekt in Visual Studio hinzuzufügen.
1. Öffnen Sie das Projekt in Visual Studio.
2. Klicken Sie mit der rechten Maustaste auf den Projektknoten, und wählen **Sie NuGet Pakete verwalten... aus.**
3. Wählen Sie im daraufhin angezeigten Bereich **Durchsuchen** aus, und suchen Sie dann nach "Holographic Remoting".
4. Wählen Sie **Microsoft.Holographic.Remoting.OpenXr aus,** wählen Sie die neueste **Version von 2.x.x** aus, und wählen **Sie Installieren** aus.
5. Wenn das Dialogfeld **Vorschau** angezeigt wird, wählen Sie **OK** aus.
6. Wählen Sie **Ich stimme zu** aus, wenn das Dialogfeld "Lizenzvertrag" angezeigt wird.
7. Wiederholen Sie die Schritte 3 bis 6 für die folgenden NuGet-Pakete: OpenXR.Headers, OpenXR.Loader

>[!NOTE]
>Version **1.x.x** des NuGet-Pakets ist weiterhin für Entwickler verfügbar, die HoloLens 1 als Ziel verwenden möchten. Weitere Informationen finden Sie unter [Hinzufügen von Holographic Remoting (HoloLens (1. Generation)).](add-holographic-remoting.md)

## <a name="select-the-holographic-remoting-openxr-runtime"></a>Wählen Sie die Holographic Remoting OpenXR-Runtime aus.

Der erste Schritt, den Sie in Ihrer Remote-App ausführen müssen, besteht darin, die Holographic Remoting OpenXR-Runtime auszuwählen, die Teil des Pakets Microsoft.Holographic.Remoting.OpenXr NuGet ist. Sie können dies erreichen, indem Sie die ```XR_RUNTIME_JSON``` Umgebungsvariable auf den Pfad der RemotingXR.jsin der Datei in Ihrer App festlegen. Diese Umgebungsvariable wird vom OpenXR-Ladeprogramm verwendet, um nicht die Standardmäßige OpenXR-Laufzeit des Systems zu verwenden, sondern zur Holographic Remoting OpenXR-Runtime umzuleiten. Bei Verwendung des Microsoft.Holographic.Remoting.OpenXr-NuGet Pakets wird die RemotingXR.jsin der Datei automatisch während der Kompilierung in den Ausgabeordner kopiert. Die OpenXR-Laufzeitauswahl sieht in der Regel wie folgt aus.

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

## <a name="create-xrinstance-with-holographic-remoting-extension"></a>Erstellen von XrInstance mit der Holographic Remoting-Erweiterung

Der erste Schritt, den eine typische OpenXR-App durchführen soll, besteht darin, OpenXR-Erweiterungen auszuwählen und eine XrInstance zu erstellen. Die OpenXR-Kernspezifikation bietet keine Remoting-spezifische API. Aus diesem Grund führt Holographic Remoting eine eigene OpenXR-Erweiterung namens ```XR_MSFT_holographic_remoting``` ein. Stellen Sie sicher, dass beim Aufrufen von xrCreateInstance ```XR_MSFT_HOLOGRAPHIC_REMOTING_EXTENSION_NAME``` in XrInstanceCreateInfo enthalten ist.

>[!TIP]
>Standardmäßig wird der gerenderte Inhalt Ihrer App nur an den Holographic Remoting-Player gestreamt, der entweder auf einem HoloLens 2 oder auf einem Windows Mixed Reality Headsets ausgeführt wird. Um den gerenderten Inhalt auch auf dem Remote-PC anzuzeigen, stellt Holographic Remoting beispielsweise über eine Austauschkette eines Fensters eine zweite OpenXR-Erweiterung mit dem Namen ```XR_MSFT_holographic_remoting_frame_mirroring``` bereit. Stellen Sie sicher, dass Sie diese Erweiterung auch mit aktivieren, ```XR_MSFT_HOLOGRAPHIC_REMOTING_FRAME_MIRRORING_EXTENSION_NAME``` falls Sie diese Funktionalität verwenden möchten.

>[!IMPORTANT]
>Informationen zur Holographic Remoting OpenXR-Erweiterungs-API finden Sie in der [Spezifikation](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html) im [GitHub-Repository holographic remoting samples (Holographic Remoting-Beispiele).](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)

## <a name="connect-to-the-device"></a>Verbinden auf das Gerät

Nachdem Ihre Remote-App die XrInstance erstellt und die XrSystemId über xrGetSystem abgefragt hat, kann eine Verbindung mit dem Playergerät hergestellt werden.

>[!WARNING]
> Die Holographic Remoting OpenXR-Runtime kann nur gerätespezifische Daten wie Ansichtskonfigurationen oder Umgebungsmischungsmodi bereitstellen, nachdem eine Verbindung hergestellt wurde. ```xrEnumerateViewConfigurations```, , , und geben Ihnen Standardwerte, die ```xrEnumerateViewConfigurationViews``` ```xrGetViewConfigurationProperties``` denen ```xrEnumerateEnvironmentBlendModes``` ```xrGetSystemProperties``` entsprechen, die Sie normalerweise erhalten würden, wenn Sie eine Verbindung mit einem Player herstellen, der auf einem HoloLens 2 ausgeführt wird, bevor sie vollständig verbunden sind.
Es wird dringend empfohlen, diese Methoden nicht aufzurufen, bevor eine Verbindung hergestellt wurde. Der Vorschlag wird mit diesen Methoden verwendet, nachdem die XrSession erfolgreich erstellt wurde und der Sitzungszustand mindestens XR_SESSION_STATE_READY ist.

Allgemeine Eigenschaften wie max bitrate, audio enabled, video codec oder depth buffer stream resolution können wie folgt konfiguriert ```xrRemotingSetContextPropertiesMSFT``` werden.

```cpp
XrRemotingRemoteContextPropertiesMSFT contextProperties;
contextProperties = XrRemotingRemoteContextPropertiesMSFT{static_cast<XrStructureType>(XR_TYPE_REMOTING_REMOTE_CONTEXT_PROPERTIES_MSFT)};
contextProperties.enableAudio = false;
contextProperties.maxBitrateKbps = 20000;
contextProperties.videoCodec = XR_REMOTING_VIDEO_CODEC_H265_MSFT;
contextProperties.depthBufferStreamResolution = XR_REMOTING_DEPTH_BUFFER_STREAM_RESOLUTION_HALF_MSFT;
xrRemotingSetContextPropertiesMSFT(m_instance.Get(), m_systemId, &contextProperties);
```

Die Verbindung kann auf zwei Arten hergestellt werden.
1) Die Remote-App stellt eine Verbindung mit dem Player her, der auf dem Gerät ausgeführt wird.
2) Der player, der auf dem Gerät ausgeführt wird, stellt eine Verbindung mit der Remote-App her.

Um eine Verbindung zwischen der Remote-App und dem Playergerät herzustellen, rufen Sie die -Methode auf, ```xrRemotingConnectMSFT``` die den Hostnamen und port über die  ```XrRemotingConnectInfoMSFT``` -Struktur angibt. Der Port, der vom Holographic Remoting Player verwendet wird, ist **8265**.

```cpp
XrRemotingConnectInfoMSFT connectInfo{static_cast<XrStructureType>(XR_TYPE_REMOTING_CONNECT_INFO_MSFT)};
connectInfo.remoteHostName = "192.168.x.x";
connectInfo.remotePort = 8265;
connectInfo.secureConnection = false;
xrRemotingConnectMSFT(m_instance.Get(), m_systemId, &connectInfo);
```

Das Lauschen auf eingehende Verbindungen in der Remote-App kann durch Aufrufen der ```xrRemotingListenMSFT``` -Methode erfolgen. Sowohl der Handshakeport als auch der Transportport können über die -Struktur angegeben ```XrRemotingListenInfoMSFT``` werden. Der Handshakeport wird für den ersten Handshake verwendet. Die Daten werden dann über den Transportport gesendet. Standardmäßig werden **8265** und **8266** verwendet.

```cpp
XrRemotingListenInfoMSFT listenInfo{static_cast<XrStructureType>(XR_TYPE_REMOTING_LISTEN_INFO_MSFT)};
listenInfo.listenInterface = "0.0.0.0";
listenInfo.handshakeListenPort = 8265;
listenInfo.transportListenPort = 8266;
listenInfo.secureConnection = false;
xrRemotingListenMSFT(m_instance.Get(), m_systemId, &listenInfo);
```

Der Verbindungsstatus muss getrennt werden, wenn Sie ```xrRemotingConnectMSFT``` oder ```xrRemotingListenMSFT``` aufrufen. Sie können den Verbindungsstatus jederzeit abrufen, nachdem Sie eine XrInstance erstellt und die XrSystemId über abgefragt ```xrRemotingGetConnectionStateMSFT``` haben.

```cpp
XrRemotingConnectionStateMSFT connectionState;
xrRemotingGetConnectionStateMSFT(m_instance.Get(), m_systemId, &connectionState, nullptr);
```

Verfügbare Verbindungszustände:
- XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT
- XR_REMOTING_CONNECTION_STATE_CONNECTING_MSFT
- XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT

>[!IMPORTANT]
> ```xrRemotingConnectMSFT``` oder ```xrRemotingListenMSFT``` muss aufgerufen werden, bevor versucht wird, eine XrSession über xrCreateSession zu erstellen. Wenn Sie versuchen, eine XrSession zu erstellen, während der Verbindungsstatus ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` lautet, ist die Sitzungserstellung erfolgreich, aber der Sitzungszustand geht sofort in XR_SESSION_STATE_LOSS_PENDING über.

Die Holographic Remoting-Implementierung von ```xrCreateSession``` unterstützt das Warten auf das Herstellen einer Verbindung. Sie können ```xrRemotingConnectMSFT``` oder direkt gefolgt von einem Aufruf von ```xrRemotingListenMSFT``` aufrufen, der blockiert und wartet, bis eine Verbindung hergestellt wird. Das Timeout ist auf 10 Sekunden festgelegt. Wenn innerhalb dieses Zeitraums eine Verbindung hergestellt werden kann, ist die XrSession-Erstellung erfolgreich, und der Sitzungszustand geht in XR_SESSION_STATE_READY über. Falls keine Verbindung hergestellt werden kann, ist die Sitzungserstellung ebenfalls erfolgreich, geht aber sofort zu XR_SESSION_STATE_LOSS_PENDING über.

Im Allgemeinen ist der Verbindungszustand mit dem XrSession-Zustand koppelt. Jede Änderung des Verbindungszustands wirkt sich auch auf den Sitzungszustand aus. Wenn beispielsweise der Verbindungszustand von in den Sitzungszustand wechselt, `XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT` wird auch in XR_SESSION_STATE_LOSS_PENDING ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` übergestellt.

## <a name="handling-remoting-specific-events"></a>Behandeln von Remoting-spezifischen Ereignissen

Die Holographic Remoting OpenXR-Runtime macht drei Ereignisse verfügbar, die wichtig sind, um den Zustand einer Verbindung zu überwachen.
1) ```XR_TYPE_REMOTING_EVENT_DATA_CONNECTED_MSFT```: Wird ausgelöst, wenn eine Verbindung mit dem Gerät erfolgreich hergestellt wurde.
2) ```XR_TYPE_REMOTING_EVENT_DATA_DISCONNECTED_MSFT```: Wird ausgelöst, wenn eine hergestellte Verbindung geschlossen wird oder keine Verbindung hergestellt werden konnte.
3) ```XR_TYPE_REMOTING_EVENT_DATA_LISTENING_MSFT```: Beim Lauschen auf eingehende Verbindungen wird gestartet.

Diese Ereignisse werden in einer Warteschlange platziert, und Ihre Remote-App muss regelmäßig über aus der Warteschlange ```xrPollEvent``` lesen.

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

## <a name="preview-streamed-content-locally"></a>Lokale Vorschau von gestreamten Inhalten

Um denselben Inhalt in der Remote-App anzuzeigen, die an das Gerät gesendet wird, kann die ```XR_MSFT_holographic_remoting_frame_mirroring``` Erweiterung verwendet werden. Mit dieser Erweiterung können Sie eine Textur an xrEndFrame übermitteln, indem Sie den ```XrRemotingFrameMirrorImageInfoMSFT``` verwenden, der nicht wie folgt mit XrFrameEndInfo verkettet ist.

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

Im obigen Beispiel wird eine DX11-Swapkettentextur verwendet, und das Fenster wird unmittelbar nach dem Aufruf von xrEndFrame dargestellt. Die Verwendung ist nicht auf Swap-Chain-Texturen beschränkt, und es ist keine zusätzliche GPU-Synchronisierung erforderlich. Ausführliche Informationen zur Verwendung und zu Einschränkungen finden Sie in der [Erweiterungsspezifikation](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html#XR_MSFT_remoting_frame_mirroring).
Wenn Ihre Remote-App DX12 verwendet, verwenden Sie XrRemotingFrameMirrorImageD3D12MSFT anstelle von XrRemotingFrameMirrorImageD3D11MSFT.

## <a name="see-also"></a>Weitere Informationen
* [Schreiben einer benutzerdefinierten Holographic Remoting Player-App](holographic-remoting-create-player.md)
* [Einrichten einer sicheren Verbindung mit Holographic Remoting](holographic-remoting-secure-connection.md)
* [Problembehandlung und Einschränkungen für Holographic Remoting](holographic-remoting-troubleshooting.md)
* [Holographic Remoting-Software – Lizenzbedingungen](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Datenschutzerklärung von Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)