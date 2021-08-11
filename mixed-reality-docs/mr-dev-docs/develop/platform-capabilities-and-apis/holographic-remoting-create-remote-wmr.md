---
title: Schreiben einer Holographic Remoting-Remote-App (WMR)
description: Erfahren Sie, wie Sie Remoteinhalte, die auf einem Remotecomputer gerendert wurden, mit Holographic Remoting-Apps mit HolographicSpace an HoloLens 2 streamen.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, Remoting, Holographic Remoting, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, NuGet
ms.openlocfilehash: 0d8f7149533de7f3f095761b13feeb91c319cda711c99b9101a13300a591fc2c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219214"
---
# <a name="writing-a-holographic-remoting-remote-app-using-the-holographicspace-api"></a>Schreiben einer Holographic Remoting-Remote-App mithilfe der HolographicSpace-API

>[!IMPORTANT]
>In diesem Dokument wird die Erstellung einer Remoteanwendung für HoloLens 2 mithilfe der [HolographicSpace-API](../native/getting-a-holographicspace.md)beschrieben. Remoteanwendungen für **HoloLens (1. Generation)** müssen NuGet Paketversion **1.x.x** verwenden. Dies bedeutet, dass Remoteanwendungen, die für HoloLens 2 geschrieben wurden, nicht mit HoloLens 1 kompatibel sind und umgekehrt. Die Dokumentation für HoloLens 1 finden Sie [hier.](add-holographic-remoting.md)

Holographic Remoting-Apps können per Remotezugriff gerenderte Inhalte an HoloLens 2 und Windows Mixed Reality immersive Headsets streamen. Sie können auch auf weitere Systemressourcen zugreifen und [immersive Remoteansichten](../../design/app-views.md) in vorhandene Desktop-PC-Software integrieren. Eine Remote-App empfängt einen Eingabedatenstrom von HoloLens 2, rendert Inhalte in einer virtuellen immersiven Ansicht und streamt Inhaltsframes zurück an HoloLens 2. Die Verbindung wird mithilfe von Standard-WLAN hergestellt. Holographic Remoting wird einer Desktop- oder UWP-App über ein NuGet Paket hinzugefügt. Es ist zusätzlicher Code erforderlich, der die Verbindung verarbeitet und in einer immersiven Ansicht rendert. Eine typische Remotingverbindung hat eine Latenz von bis zu 50 ms. Die Player-App kann die Latenz in Echtzeit melden.

Den gesamten Code auf dieser Seite und funktionierende Projekte finden Sie im [GitHub-Repository für Holographic Remoting-Beispiele.](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)

## <a name="prerequisites"></a>Voraussetzungen

Ein guter Ausgangspunkt ist eine funktionierende DirectX-basierte Desktop- oder UWP-App, die auf die [HolographicSpace-API](../native/getting-a-holographicspace.md)ausgerichtet ist. Weitere Informationen finden Sie unter [Übersicht über die DirectX-Entwicklung.](../native/directx-development-overview.md) Die [holografische C++-Projektvorlage](../native/creating-a-holographic-directx-project.md) ist ein guter Ausgangspunkt.

>[!IMPORTANT]
>Jede App, die Holographic Remoting verwendet, sollte so erstellt werden, dass sie ein [Multithread-Apartment](/windows/win32/com/multithreaded-apartments)verwendet. Die Verwendung eines [Singlethread-Apartments](/windows/win32/com/single-threaded-apartments) wird unterstützt, führt aber zu einer suboptimalen Leistung und möglicherweise zu einem Stubing während der Wiedergabe. Bei Verwendung von C++/WinRT [winrt::init_apartment](/windows/uwp/cpp-and-winrt-apis/get-started) ist ein Multithread-Apartment die Standardeinstellung.



## <a name="get-the-holographic-remoting-nuget-package"></a>Abrufen des Holographic Remoting NuGet-Pakets

Die folgenden Schritte sind erforderlich, um das NuGet-Paket einem Projekt in Visual Studio hinzuzufügen.
1. Öffnen Sie das Projekt in Visual Studio.
2. Klicken Sie mit der rechten Maustaste auf den Projektknoten, und wählen **Sie NuGet Pakete verwalten... aus.**
3. Wählen Sie im daraufhin angezeigten Bereich **Durchsuchen** aus, und suchen Sie dann nach "Holographic Remoting".
4. Wählen Sie **Microsoft.Holographic.Remoting** aus, wählen Sie die neueste **Version von 2.x.x** aus, und wählen **Sie Installieren** aus.
5. Wenn das Dialogfeld **Vorschau** angezeigt wird, wählen Sie **OK** aus.
6. Wählen Sie **Ich stimme zu** aus, wenn das Dialogfeld "Lizenzvertrag" angezeigt wird.

>[!NOTE]
>Version **1.x.x** des NuGet-Pakets ist weiterhin für Entwickler verfügbar, die HoloLens 1 als Ziel verwenden möchten. Weitere Informationen finden Sie unter [Hinzufügen von Holographic Remoting (HoloLens (1. Generation)).](add-holographic-remoting.md)

## <a name="create-the-remote-context"></a>Erstellen des Remotekontexts

Als ersten Schritt sollte die Anwendung einen Remotekontext erstellen.

```cpp
// class declaration
#include <winrt/Microsoft.Holographic.AppRemoting.h>

...

private:
    // RemoteContext used to connect with a Holographic Remoting player and display rendered frames
    winrt::Microsoft::Holographic::AppRemoting::RemoteContext m_remoteContext = nullptr;
```


```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

```

>[!WARNING]
>Holographic Remoting ersetzt die Windows Mixed Reality Runtime, die Teil Windows ist, durch eine Remoting-spezifische Runtime. Dies erfolgt während der Erstellung des Remotekontexts. Aus diesem Grund kann jeder Aufruf einer beliebigen Windows Mixed Reality-API vor dem Erstellen des Remotekontexts zu unerwartetem Verhalten führen. Der empfohlene Ansatz besteht darin, den Remotekontext so früh wie möglich vor der Interaktion mit einer beliebigen Mixed Reality-API zu erstellen. Mischen Sie niemals Objekte, die über eine Windows Mixed Reality-API erstellt oder abgerufen wurden, vor dem Aufruf von CreateRemoteContext mit Objekten, die anschließend erstellt oder abgerufen werden.

Als Nächstes muss der holografische Raum erstellt werden. Die Angabe eines CoreWindow ist nicht erforderlich. Desktop-Apps ohne CoreWindow können einfach eine ```nullptr``` übergeben.

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(nullptr);
```

## <a name="connect-to-the-device"></a>Verbinden auf das Gerät

Wenn die Remote-App zum Rendern von Inhalten bereit ist, kann eine Verbindung mit dem Playergerät hergestellt werden.

Die Verbindung kann auf zwei Arten hergestellt werden.
1) Die Remote-App stellt eine Verbindung mit dem Player her, der auf dem Gerät ausgeführt wird.
2) Der player, der auf dem Gerät ausgeführt wird, stellt eine Verbindung mit der Remote-App her.

Um eine Verbindung zwischen der Remote-App und dem Playergerät herzustellen, rufen Sie die ```Connect``` -Methode im Remotekontext auf, und geben Sie den Hostnamen und den Port an. Der Port, der vom Holographic Remoting Player verwendet wird, ist **8265**.

```cpp
try
{
    m_remoteContext.Connect(m_hostname, m_port);
}
catch(winrt::hresult_error& e)
{
    DebugLog(L"Connect failed with hr = 0x%08X", e.code());
}
```

>[!IMPORTANT]
>Wie bei jeder C++/WinRT-API ```Connect``` kann eine winrt::hresult_error ausgelöst werden, die behandelt werden muss.

>[!TIP]
>Um die Verwendung der [C++/WinRT-Sprachprojektion](/windows/uwp/cpp-and-winrt-apis/) zu vermeiden, kann die Datei ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` im Holographic Remoting-NuGet Paket enthalten sein. Sie enthält Deklarationen der zugrunde liegenden COM-Schnittstellen. Die Verwendung von C++/WinRT wird jedoch empfohlen.

Das Lauschen auf eingehende Verbindungen in der Remote-App kann durch Aufrufen der ```Listen``` -Methode erfolgen. Sowohl der Handshakeport als auch der Transportport können während dieses Aufrufs angegeben werden. Der Handshakeport wird für den ersten Handshake verwendet. Die Daten werden dann über den Transportport gesendet. Standardmäßig werden **8265** und **8266** verwendet.

```cpp
try
{
    m_remoteContext.Listen(L"0.0.0.0", m_port, m_port + 1);
}
catch(winrt::hresult_error& e)
{
    DebugLog(L"Listen failed with hr = 0x%08X", e.code());
}
```

>[!IMPORTANT]
>Die ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` im NuGet Paket enthält eine ausführliche Dokumentation für die API, die von Holographic Remoting verfügbar gemacht wird.

## <a name="handling-remoting-specific-events"></a>Behandeln von Remoting-spezifischen Ereignissen

Der Remotekontext macht drei Ereignisse verfügbar, die wichtig sind, um den Zustand einer Verbindung zu überwachen.
1) OnConnected: Wird ausgelöst, wenn eine Verbindung mit dem Gerät erfolgreich hergestellt wurde.
```cpp
winrt::weak_ref<winrt::Microsoft::Holographic::AppRemoting::IRemoteContext> remoteContextWeakRef = m_remoteContext;

m_onConnectedEventRevoker = m_remoteContext.OnConnected(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```
2) OnDisconnected: Wird ausgelöst, wenn eine hergestellte Verbindung geschlossen wird oder keine Verbindung hergestellt werden konnte.
```cpp
m_onDisconnectedEventRevoker =
    m_remoteContext.OnDisconnected(winrt::auto_revoke, [this, remoteContextWeakRef](ConnectionFailureReason failureReason) {
        if (auto remoteContext = remoteContextWeakRef.get())
        {
            DebugLog(L"Disconnected with reason %d", failureReason);
            // Update UI

            // Reconnect if this is a transient failure.
            if (failureReason == ConnectionFailureReason::HandshakeUnreachable ||
                failureReason == ConnectionFailureReason::TransportUnreachable ||
                failureReason == ConnectionFailureReason::ConnectionLost)
            {
                DebugLog(L"Reconnecting...");

                ConnectOrListen();
            }
            // Failure reason None indicates a normal disconnect.
            else if (failureReason != ConnectionFailureReason::None)
            {
                DebugLog(L"Disconnected with unrecoverable error, not attempting to reconnect.");
            }
        }
    });
```
3) OnListening: Beim Lauschen auf eingehende Verbindungen wird gestartet.
```cpp
m_onListeningEventRevoker = m_remoteContext.OnListening(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```

Darüber hinaus kann der Verbindungszustand mithilfe der ```ConnectionState``` -Eigenschaft im Remotekontext abgefragt werden.
```cpp
auto connectionState = m_remoteContext.ConnectionState();
```

## <a name="handling-speech-events"></a>Behandeln von Sprachereignissen

Mithilfe der Remote speech-Schnittstelle können Sprachtrigger bei HoloLens 2 registriert und per Remotezugriff an die Remoteanwendung übertragen werden.

Dieses zusätzliche Element ist erforderlich, um den Zustand der Remotesprache nachzuverfolgen.

```cpp
winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker m_onRecognizedSpeechRevoker;

```

Zuerst muss die Remote speech-Schnittstelle abgerufen werden.

```cpp
if (auto remoteSpeech = m_remoteContext.GetRemoteSpeech())
{
    InitializeSpeechAsync(remoteSpeech, m_onRecognizedSpeechRevoker, weak_from_this());
}
```

Mithilfe einer asynchronen Hilfsmethode können Sie dann die Remotesprache initialisieren. Dies sollte asynchron erfolgen, da die Initialisierung viel Zeit in Anspruch nehmen kann. [Parallelität und asynchrone Vorgänge mit C++/WinRT](/windows/uwp/cpp-and-winrt-apis/concurrency) erläutert, wie asynchrone Funktionen mit C++/WinRT erstellt werden.

```cpp
winrt::Windows::Foundation::IAsyncOperation<winrt::Windows::Storage::StorageFile> LoadGrammarFileAsync()
{
    const wchar_t* speechGrammarFile = L"SpeechGrammar.xml";
    auto rootFolder = winrt::Windows::ApplicationModel::Package::Current().InstalledLocation();
    return rootFolder.GetFileAsync(speechGrammarFile);
}

winrt::fire_and_forget InitializeSpeechAsync(
    winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech remoteSpeech,
    winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker& onRecognizedSpeechRevoker,
    std::weak_ptr<SampleRemoteMain> sampleRemoteMainWeak)
{
    onRecognizedSpeechRevoker = remoteSpeech.OnRecognizedSpeech(
        winrt::auto_revoke, [sampleRemoteMainWeak](const winrt::Microsoft::Holographic::AppRemoting::RecognizedSpeech& recognizedSpeech) {
            if (auto sampleRemoteMain = sampleRemoteMainWeak.lock())
            {
                sampleRemoteMain->OnRecognizedSpeech(recognizedSpeech.RecognizedText);
            }
        });

    auto grammarFile = co_await LoadGrammarFileAsync();

    std::vector<winrt::hstring> dictionary;
    dictionary.push_back(L"Red");
    dictionary.push_back(L"Blue");
    dictionary.push_back(L"Green");
    dictionary.push_back(L"Default");
    dictionary.push_back(L"Aquamarine");

    remoteSpeech.ApplyParameters(L"", grammarFile, dictionary);
}
```

Es gibt zwei Möglichkeiten, Ausdrücke anzugeben, die erkannt werden sollen.
1) Spezifikation in einer XML-Datei für die Sprachgrammatik. Weitere Informationen finden Sie unter [Erstellen einer einfachen XML-Grammatik.](/previous-versions/office/developer/speech-technologies/hh361658(v=office.14))
2) Geben Sie an, indem Sie sie innerhalb des Wörterbuchvektors an ```ApplyParameters``` übergeben.

Innerhalb des OnRecognizedSpeech-Rückrufs können die Sprachereignisse verarbeitet werden:

```cpp
void SampleRemoteMain::OnRecognizedSpeech(const winrt::hstring& recognizedText)
{
    bool changedColor = false;
    DirectX::XMFLOAT4 color = {1, 1, 1, 1};

    if (recognizedText == L"Red")
    {
        color = {1, 0, 0, 1};
        changedColor = true;
    }
    else if (recognizedText == L"Blue")
    {
        color = {0, 0, 1, 1};
        changedColor = true;
    }
    else if (recognizedText == L"Green")
    {
        ...
    }

    ...
}
```

## <a name="preview-streamed-content-locally"></a>Lokale Vorschau von gestreamten Inhalten

Um den gleichen Inhalt in der Remote-App anzuzeigen, die an das Gerät gesendet wird, kann das ```OnSendFrame``` Ereignis des Remotekontexts verwendet werden. Das ```OnSendFrame``` Ereignis wird jedes Mal ausgelöst, wenn die Holographic Remoting-Bibliothek den aktuellen Frame an das Remotegerät sendet. Dies ist der ideale Zeitpunkt, um den Inhalt zu verwenden und ihn auch in das Desktop- oder UWP-Fenster zu integrieren.

```cpp
#include <windows.graphics.directx.direct3d11.interop.h>

...

m_onSendFrameEventRevoker = m_remoteContext.OnSendFrame(
    winrt::auto_revoke, [this](const winrt::Windows::Graphics::DirectX::Direct3D11::IDirect3DSurface& texture) {
        winrt::com_ptr<ID3D11Texture2D> texturePtr;
        {
            winrt::com_ptr<ID3D11Resource> resource;
            winrt::com_ptr<::IInspectable> inspectable = texture.as<::IInspectable>();
            winrt::com_ptr<Windows::Graphics::DirectX::Direct3D11::IDirect3DDxgiInterfaceAccess> dxgiInterfaceAccess;
            winrt::check_hresult(inspectable->QueryInterface(__uuidof(dxgiInterfaceAccess), dxgiInterfaceAccess.put_void()));
            winrt::check_hresult(dxgiInterfaceAccess->GetInterface(__uuidof(resource), resource.put_void()));
            resource.as(texturePtr);
        }

        // Copy / blit texturePtr into the back buffer here.
    });
```

## <a name="depth-reprojection"></a>Tiefenreprojektion

Ab Version [2.1.0](holographic-remoting-version-history.md#v2.1.0)unterstützt Holographic Remoting [depth reprojection](hologram-stability.md#reprojection). Dies erfordert, dass sowohl der Farbpuffer als auch der Tiefenpuffer von der Remoteanwendung an die HoloLens 2 gestreamt werden. Standardmäßig ist das Tiefenpufferstreaming aktiviert und so konfiguriert, dass die Hälfte der Auflösung des Farbpuffers verwendet wird. Dies kann wie folgt geändert werden:

```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

// Configure for half-resolution depth.
m_remoteContext.ConfigureDepthVideoStream(DepthBufferStreamResolution::Half_Resolution);

```

Hinweis: Wenn keine Standardwerte verwendet werden sollen, ```ConfigureDepthVideoStream``` muss aufgerufen werden, bevor eine Verbindung mit dem HoloLens 2 hergestellt wird. Der beste Ort ist direkt nach dem Erstellen des Remotekontexts. Mögliche Werte für DepthBufferStreamResolution sind:

* Full_Resolution
* Half_Resolution
* Quarter_Resolution
* Deaktiviert (hinzugefügt mit Version [2.1.3](holographic-remoting-version-history.md#v2.1.3) und bei Verwendung wird kein zusätzlicher Tiefenvideostream erstellt)

Beachten Sie, dass sich die Verwendung eines tiefen Puffers mit vollständiger Auflösung auch auf die Bandbreitenanforderungen auswirkt und im maximalen Bandbreitenwert berücksichtigt werden muss, den Sie für ```CreateRemoteContext``` angeben.

Neben der Konfiguration der Auflösung müssen Sie auch einen Tiefenpuffer über [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer committen.](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)

```cpp

void SampleRemoteMain::Render(HolographicFrame holographicFrame)
{
    ...

    m_deviceResources->UseHolographicCameraResources([this, holographicFrame](auto& cameraResourceMap) {
        
        ...

        for (auto cameraPose : prediction.CameraPoses())
        {
            DXHelper::CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();

            ...

            m_deviceResources->UseD3DDeviceContext([&](ID3D11DeviceContext3* context) {
                
                ...

                // Commit depth buffer if available and enabled.
                if (m_canCommitDirect3D11DepthBuffer && m_commitDirect3D11DepthBuffer)
                {
                    auto interopSurface = pCameraResources->GetDepthStencilTextureInteropObject();
                    HolographicCameraRenderingParameters renderingParameters = holographicFrame.GetRenderingParameters(cameraPose);
                    renderingParameters.CommitDirect3D11DepthBuffer(interopSurface);
                }
            });
        }
    });
}

```

Um zu überprüfen, ob die Tiefenreprojektion ordnungsgemäß an HoloLens 2 funktioniert, können Sie eine Tiefenansicht über die Geräteportal aktivieren. Weitere Informationen finden Sie unter [Überprüfen, ob die Tiefe richtig festgelegt ist.](hologram-stability.md#verifying-depth-is-set-correctly)

## <a name="optional-custom-data-channels"></a>Optional: Benutzerdefinierte Datenkanäle

Benutzerdefinierte Datenkanäle können verwendet werden, um Benutzerdaten über die bereits eingerichtete Remotingverbindung zu senden. Weitere Informationen finden Sie [unter Benutzerdefinierte Datenkanäle.](holographic-remoting-custom-data-channels.md)

## <a name="see-also"></a>Weitere Informationen
* [Schreiben einer benutzerdefinierten Holographic Remoting Player-App](holographic-remoting-create-player.md)
* [Benutzerdefinierte Holographic Remoting-Datenkanäle](holographic-remoting-custom-data-channels.md)
* [Einrichten einer sicheren Verbindung mit Holographic Remoting](holographic-remoting-secure-connection.md)
* [Problembehandlung und Einschränkungen für Holographic Remoting](holographic-remoting-troubleshooting.md)
* [Holographic Remoting-Software – Lizenzbedingungen](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Datenschutzerklärung von Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)