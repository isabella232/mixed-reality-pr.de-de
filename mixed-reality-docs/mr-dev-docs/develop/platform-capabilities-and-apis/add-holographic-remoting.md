---
title: Hinzufügen von holografischem Remoting
description: Erfahren Sie, wie Sie Holographic Remoting installieren, konfigurieren und verwenden, um Hologramme auf einem HoloLens über das Netzwerk zu rendern.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: Windows Mixed Reality, Hologramme, holografisches Remoting, Remoterendering, Netzwerkrendering, HoloLens, Remote hologramme, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 3f9d3d23d18f680ce1001310e4ce49089edaae6a
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2021
ms.locfileid: "122184621"
---
# <a name="add-holographic-remoting-hololens-first-gen"></a>Hinzufügen von Holographic Remoting (HoloLens (erste Generation))

>[!IMPORTANT]
> In diesem Dokument wird die Erstellung einer Hostanwendung für HoloLens 1 beschrieben. Hostanwendung für **HoloLens (1. Generation)** muss NuGet **Paketversion 1.x.x verwenden.** Dies bedeutet, dass Hostanwendungen, die für HoloLens 1 geschrieben wurden, nicht mit HoloLens 2 und umgekehrt kompatibel sind.

## <a name="hololens-2"></a>HoloLens 2

HoloLens, die Holographic Remoting verwenden, müssen ihre Apps aktualisieren, damit sie mit den HoloLens 2. Dies erfordert eine neue Version des Holographic Remoting NuGet Pakets. Stellen Sie sicher, dass Sie Version 2.0.0.0 oder höher des Holographic Remoting NuGet-Pakets verwenden, wenn Sie eine Verbindung mit dem Holographic Remoting Player auf HoloLens 2 herstellen, da die Verbindung fehlschlägt.

>[!NOTE]
> Spezifische Anleitungen für HoloLens 2 finden Sie [hier.](holographic-remoting-create-remote-wmr.md)


## <a name="add-holographic-remoting-to-your-desktop-or-uwp-app"></a>Hinzufügen von holografischem Remoting zu Ihrem Desktop oder Ihrer UWP-App

Auf dieser Seite wird beschrieben, wie Holographic Remoting einer Desktop- oder UWP-App hinzugefügt wird.

Mit Holographic Remoting kann Ihre App auf eine HoloLens mit holografischen Inhalten ausgerichtet werden, die auf einem Desktop-PC oder auf einem UWP-Gerät wie dem Xbox One. Sie haben auch Zugriff auf weitere Systemressourcen, wodurch sie die Integration von immersiven Remoteansichten [in](../../design/app-views.md) vorhandene Desktop-PC-Software ermöglichen. Eine Remotinghost-App empfängt einen Eingabedatenstrom von einem HoloLens, rendert Inhalte in einer virtuellen immersiven Ansicht und streamt Inhaltsframes zurück an HoloLens. Die Verbindung wird mithilfe von STANDARD-WLAN hergestellt. Um Remoting zu verwenden, verwenden Sie ein NuGet-Paket, um Ihrem Desktop oder Ihrer UWP-App holografisches Remoting hinzuzufügen. Schreiben Sie dann Code, um die Verbindung zu verarbeiten und eine immersive Ansicht zu rendern. Hilfsbibliotheken sind im Codebeispiel enthalten, die die Verarbeitung der Geräteverbindung vereinfachen.

Eine typische Remotingverbindung hat eine Latenz von bis zu 50 ms. Die Player-App kann die Latenzzeit in Echtzeit melden.

>[!NOTE]
>Die Codeausschnitte in diesem Artikel veranschaulichen derzeit die Verwendung von C++/CX anstelle von C++17-kompatiblem C++/WinRT, wie in der holografischen C++-Projektvorlage [verwendet.](../native/creating-a-holographic-directx-project.md)  Die Konzepte sind für ein C++/WinRT-Projekt gleichwertig, obwohl Sie den Code übersetzen müssen.

### <a name="get-the-remoting-nuget-packages"></a>Get the remoting NuGet packages

Führen Sie die folgenden Schritte aus, um NuGet Paket für holografisches Remoting zu erhalten, und fügen Sie einen Verweis aus Ihrem Projekt hinzu:
1. Wechseln Sie zu Ihrem Projekt in Visual Studio.
2. Klicken Sie mit der rechten Maustaste auf den Projektknoten, und wählen **Sie manage NuGet Packages... (Pakete verwalten) aus.**
3. Wählen Sie im angezeigten Bereich Durchsuchen aus, **und** suchen Sie dann nach "Holographic Remoting".
4. Wählen **Sie Microsoft.Holographic.Remoting aus,** und wählen Sie **Installieren aus.**
5. Wenn das **Dialogfeld Vorschau** angezeigt wird, wählen Sie **OK aus.**
6. Wählen Sie **Ich stimme zu** aus, wenn das Dialogfeld lizenzvertrag angezeigt wird.

### <a name="create-the-holographicstreamerhelpers"></a>Erstellen der HolographicStreamerHelpers

Zunächst müssen wir der Klasse eine Instanz von HolographicStreamerHelpers hinzufügen, die Remoting behandelt.

```cpp
#include <HolographicStreamerHelpers.h>

   private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;
```

Außerdem müssen Sie den Verbindungsstatus nachverfolgen. Wenn Sie die Vorschau rendern möchten, benötigen Sie eine Textur, in die sie kopiert werden kann. Außerdem benötigen Sie einige Dinge wie eine Verbindungsstatussperre, eine Möglichkeit zum Speichern der IP-Adresse HoloLens und so weiter.

```cpp
private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;

       Microsoft::WRL::Wrappers::SRWLock                   m_connectionStateLock;

       RemotingHostSample::AppView^                        m_appView;
       Platform::String^                                   m_ipAddress;
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;

       Microsoft::WRL::Wrappers::CriticalSection           m_deviceLock;
       Microsoft::WRL::ComPtr<IDXGISwapChain1>             m_swapChain;
       Microsoft::WRL::ComPtr<ID3D11Texture2D>             m_spTexture;
```

### <a name="initialize-holographicstreamerhelpers-and-connect-to-hololens"></a>Initialisieren Sie HolographicStreamerHelpers, und stellen Sie eine Verbindung mit HoloLens

Um eine Verbindung mit einem HoloLens herzustellen, erstellen Sie eine Instanz von HolographicStreamerHelpers, und stellen Sie eine Verbindung mit der ZIEL-IP-Adresse herstellen. Sie müssen die Größe des Videoframes so festlegen, dass sie mit der HoloLens-Anzeigebreite und -höhe übereinstimmen, da die Holographic Remoting-Bibliothek erwartet, dass die Encoder- und Decoderauflösungen genau übereinstimmen.

```cpp
m_streamerHelpers = ref new HolographicStreamerHelpers();
       m_streamerHelpers->CreateStreamer(m_d3dDevice);

       // We currently need to stream at 720p because that's the resolution of our remote display.
       // There is a check in the holographic streamer that makes sure the remote and local
       // resolutions match. The default streamer resolution is 1080p.
       m_streamerHelpers->SetVideoFrameSize(1280, 720);

       try
       {
           m_streamerHelpers->Connect(m_ipAddress->Data(), 8001);
       }
       catch (Platform::Exception^ ex)
       {
           DebugLog(L"Connect failed with hr = 0x%08X", ex->HResult);
       }
```

Die Geräteverbindung ist asynchron. Ihre App muss Ereignishandler für Verbindungs-, Trennungs- und Frame-Sendeereignisse bereitstellen.

Das OnConnected-Ereignis kann die Benutzeroberfläche aktualisieren, das Rendering starten und so weiter. In unserem Desktopcodebeispiel aktualisieren wir den Fenstertitel mit einer "verbundenen" Meldung.

```cpp
m_streamerHelpers->OnConnected += ref new ConnectedEvent(
           [this]()
           {
               UpdateWindowTitle();
           });
```

Das OnDisconnected-Ereignis kann die wiederhergestellte Verbindung, Aktualisierungen der Benutzeroberfläche und so weiter verarbeiten. In diesem Beispiel stellen wir die Verbindung wieder her, wenn ein vorübergehender Fehler vor liegt.

```cpp
Platform::WeakReference streamerHelpersWeakRef = Platform::WeakReference(m_streamerHelpers);
       m_streamerHelpers->OnDisconnected += ref new DisconnectedEvent(
           [this, streamerHelpersWeakRef](_In_ HolographicStreamerConnectionFailureReason failureReason)
           {
               DebugLog(L"Disconnected with reason %d", failureReason);
               UpdateWindowTitle();

               // Reconnect if this is a transient failure.
               if (failureReason == HolographicStreamerConnectionFailureReason::Unreachable ||
                   failureReason == HolographicStreamerConnectionFailureReason::ConnectionLost)
               {
                   DebugLog(L"Reconnecting...");

                   try
                   {
                       auto helpersResolved = streamerHelpersWeakRef.Resolve<HolographicStreamerHelpers>();
                       if (helpersResolved)
                       {
                           helpersResolved->Connect(m_ipAddress->Data(), 8001);
                       }
                       else
                       {
                           DebugLog(L"Failed to reconnect because a disconnect has already occurred.\n");
                       }
                   }
                   catch (Platform::Exception^ ex)
                   {
                       DebugLog(L"Connect failed with hr = 0x%08X", ex->HResult);
                   }
               }
               else
               {
                   DebugLog(L"Disconnected with unrecoverable error, not attempting to reconnect.");
               }
           });
```

Wenn die Remotingkomponente bereit ist, einen Frame zu senden, hat Ihre App die Möglichkeit, eine Kopie davon im SendFrameEvent zu erstellen. Hier kopieren wir den Frame in eine Auslagerungskette, damit wir ihn in einem Vorschaufenster anzeigen können.

```cpp
m_streamerHelpers->OnSendFrame += ref new SendFrameEvent(
           [this](_In_ const ComPtr<ID3D11Texture2D>& spTexture, _In_ FrameMetadata metadata)
           {
               if (m_showPreview)
               {
                   ComPtr<ID3D11Device1> spDevice = m_appView->GetDeviceResources()->GetD3DDevice();
                   ComPtr<ID3D11DeviceContext> spContext = m_appView->GetDeviceResources()->GetD3DDeviceContext();

                   ComPtr<ID3D11Texture2D> spBackBuffer;
                   ThrowIfFailed(m_swapChain->GetBuffer(0, IID_PPV_ARGS(&spBackBuffer)));

                   spContext->CopySubresourceRegion(
                       spBackBuffer.Get(), // dest
                       0,                  // dest subresource
                       0, 0, 0,            // dest x, y, z
                       spTexture.Get(),    // source
                       0,                  // source subresource
                       nullptr);           // source box, null means the entire resource

                   DXGI_PRESENT_PARAMETERS parameters = { 0 };
                   ThrowIfFailed(m_swapChain->Present1(1, 0, &parameters));
               }
           });
```

### <a name="render-holographic-content"></a>Rendern von holografischem Inhalt

Um Inhalte mithilfe von Remoting zu rendern, richten Sie eine virtuelle IFrameworkView in Ihrem Desktop oder ihrer UWP-App ein und verarbeiten holografische Frames aus Remoting. Alle Windows Holographic-APIs werden in dieser Ansicht auf die gleiche Weise verwendet, aber sie sind etwas anders eingerichtet.

Anstatt sie selbst zu erstellen, stammen der holografische Raum und die Sprachkomponenten aus Ihrer HolographicRemotingHelpers-Klasse:

```cpp
m_appView->Initialize(m_streamerHelpers->HolographicSpace, m_streamerHelpers->RemoteSpeech);
```

Anstatt eine Updateschleife in einer Run-Methode zu verwenden, stellen Sie Tickupdates aus der Hauptschleife Ihres Desktops oder Ihrer UWP-App bereit. Dadurch kann Ihr Desktop oder Ihre UWP-App die Kontrolle über die Nachrichtenverarbeitung erhalten.

```cpp
void DesktopWindow::Tick()
   {
       auto lock = m_deviceLock.Lock();
       m_appView->Tick();

       // display preview, etc.
   }
```

Die Tick()-Methode der holografischen App-Ansicht schließt eine Iteration der Update-, Draw- und Present-Schleife ab.

```cpp
void AppView::Tick()
   {
       if (m_main)
       {
           // When running on Windows Holographic, we can use the holographic rendering system.
           HolographicFrame^ holographicFrame = m_main->Update();

           if (holographicFrame && m_main->Render(holographicFrame))
           {
               // The holographic frame has an API that presents the swap chain for each
               // holographic camera.
               m_deviceResources->Present(holographicFrame);
           }
       }
   }
```

Die Update-, Render- und Present-Schleife der holografischen App-Ansicht ist identisch mit der Ausführung auf HoloLens– mit der Ausnahme, dass Sie auf Ihrem Desktop-PC auf eine viel größere Menge von Systemressourcen zugreifen können. Sie können viele weitere Dreiecke rendern, mehr Zeichenläufe haben, mehr Physikalisches tun und x64-Prozesse verwenden, um Inhalte zu laden, die mehr als 2 GB RAM erfordern.

### <a name="disconnect-and-end-the-remote-session"></a>Trennen und Beenden der Remotesitzung

Um die Verbindung zu trennen, z. B. wenn der Benutzer auf eine Benutzeroberflächenschaltfläche klickt, um die Verbindung zu trennen, rufen Sie Disconnect() für HolographicStreamerHelpers auf, und geben Sie dann das Objekt frei.

```cpp
void DesktopWindow::DisconnectFromRemoteDevice()
   {
       // Disconnecting from the remote device can change the connection state.
       auto exclusiveLock = m_connectionStateLock.LockExclusive();

       if (m_streamerHelpers != nullptr)
       {
           m_streamerHelpers->Disconnect();

           // Reset state
           m_streamerHelpers = nullptr;
       }
   }
```

## <a name="get-the-remoting-player"></a>Get the remoting player (Remotingplayer erhalten)

Der Windows Holographic-Remotingplayer wird im Windows App Store als Endpunkt für Remotinghost-Apps zum Herstellen einer Verbindung angeboten. Um den Windows Holographic-Remoting-Player zu erhalten, besuchen Sie den Windows App Store aus Ihrem HoloLens, suchen Sie nach Remoting, und laden Sie die App herunter. Der Remotingplayer enthält ein Feature zum Anzeigen von Statistiken auf dem Bildschirm, was beim Debuggen von Remotinghost-Apps nützlich sein kann.

## <a name="notes-and-resources"></a>Hinweise und Ressourcen

Die holografische App-Ansicht benötigt eine Möglichkeit, um Ihrer App das Direct3D-Gerät zur Verfügung zu stellen, das zum Initialisieren des holografischen Raums verwendet werden muss. Ihre App sollte dieses Direct3D-Gerät verwenden, um den Vorschauframe zu kopieren und anzuzeigen.

```cpp
internal:
       const std::shared_ptr<DX::DeviceResources>& GetDeviceResources()
       {
           return m_deviceResources;
       }
```

**Codebeispiel:** Ein vollständiges [Holographic Remoting-Codebeispiel](https://github.com/Microsoft/HoloLensCompanionKit) ist verfügbar, das eine holografische Anwendungsansicht enthält, die mit Remoting- und Remotinghostprojekten für Desktop-Win32, UWP DirectX und UWP mit XAML kompatibel ist. 

**Debughinweis:** Die Holographic Remoting-Bibliothek kann Ausnahmen der ersten Chance auslösen. Diese Ausnahmen können in Debugsitzungen sichtbar sein, je nach Visual Studio Ausnahmeeinstellungen, die zu diesem Zeitpunkt aktiv sind. Diese Ausnahmen werden intern von der Holographic Remoting-Bibliothek erfasst und können ignoriert werden.

## <a name="see-also"></a>Weitere Informationen
* [Übersicht über Holographic Remoting](holographic-remoting-overview.md)
* [Schreiben einer benutzerdefinierten Holographic Remoting Player-App](holographic-remoting-create-player.md)
* [Einrichten einer sicheren Verbindung mit Holographic Remoting](holographic-remoting-secure-connection.md)
* [Problembehandlung und Einschränkungen bei Holographic Remoting](holographic-remoting-troubleshooting.md)
* [Holographic Remoting-Software – Lizenzbedingungen](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Datenschutzerklärung von Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)