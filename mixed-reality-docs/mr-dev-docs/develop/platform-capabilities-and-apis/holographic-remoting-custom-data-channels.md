---
title: Benutzerdefinierte Holographic Remoting-Datenkanäle
description: Benutzerdefinierte Datenkanäle können verwendet werden, um Benutzerdaten über die bereits eingerichtete Holographic Remoting-Verbindung zu senden.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, Remoting, Holographic Remoting, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Datenkanäle
ms.openlocfilehash: 09fea161f9042d7afc59c16d3b5e8a6c69892e84b1de5e9ab4a4808733b4f171
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217086"
---
# <a name="custom-holographic-remoting-data-channels"></a>Benutzerdefinierte Holographic Remoting-Datenkanäle

>[!NOTE]
>Dieser Leitfaden gilt speziell für Holographic Remoting auf HoloLens 2.

Verwenden Sie benutzerdefinierte Datenkanäle, um benutzerdefinierte Daten über eine eingerichtete Remotingverbindung zu senden.

>[!IMPORTANT]
>Benutzerdefinierte Datenkanäle erfordern eine benutzerdefinierte Remote-App und eine benutzerdefinierte Player-App, da sie die Kommunikation zwischen den beiden benutzerdefinierten Apps ermöglicht.

>[!TIP]
>Ein einfaches ping-pong-Beispiel finden Sie in den Remote- und Playerbeispielen im [GitHub-Repository holografische Remotingbeispiele](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples). Aufheben der Auskommentierung ```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE``` in den Dateien SampleRemoteMain.h/SamplePlayerMain.h, um den Beispielcode zu aktivieren.


## <a name="create-a-custom-data-channel"></a>Erstellen eines benutzerdefinierten Datenkanals


Zum Erstellen eines benutzerdefinierten Datenkanals sind die folgenden Felder erforderlich:
```cpp
std::recursive_mutex m_customDataChannelLock;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel m_customDataChannel = nullptr;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnDataReceived_revoker m_customChannelDataReceivedEventRevoker;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnClosed_revoker m_customChannelClosedEventRevoker;
```

Nachdem eine Verbindung erfolgreich hergestellt wurde, können Sie neue Datenkanäle entweder von der Remoteseite, der Playerseite oder von beiden erstellen. Sowohl RemoteContext als auch PlayerContext stellen eine ```CreateDataChannel()``` Methode zum Erstellen von Datenkanälen bereit. Der erste Parameter ist die Kanal-ID, die verwendet wird, um den Datenkanal in nachfolgenden Vorgängen zu identifizieren. Der zweite Parameter ist die Priorität, die die Priorität angibt, mit der Daten dieses Kanals auf die andere Seite übertragen werden. Gültige Kanal-IDs auf der Remoteseite reichen von 0 bis einschließlich 63 und 64 bis einschließlich 127 für die Playerseite. Gültige Prioritäten sind ```Low``` , ```Medium``` oder ```High``` (auf beiden Seiten).

So starten Sie die Erstellung eines Datenkanals auf der **Remoteseite**
```cpp
// Valid channel ids for channels created on the remote side are 0 up to and including 63
m_remoteContext.CreateDataChannel(0, DataChannelPriority::Low);
```

So starten Sie die Erstellung eines Datenkanals auf **Playerseite:**
```cpp
// Valid channel ids for channels created on the player side are 64 up to and including 127
m_playerContext.CreateDataChannel(64, DataChannelPriority::Low);
```

>[!NOTE]
>Um einen neuen benutzerdefinierten Datenkanal zu erstellen, muss nur eine Seite (remote oder player) die ```CreateDataChannel``` -Methode aufrufen.

## <a name="handling-custom-data-channel-events"></a>Behandeln von benutzerdefinierten Datenkanalereignissen

Um einen benutzerdefinierten Datenkanal einzurichten, muss das ```OnDataChannelCreated``` Ereignis behandelt werden (sowohl auf der Player- als auch auf der Remoteseite). Er wird ausgelöst, wenn ein Benutzerdatenkanal von beiden Seiten erstellt wurde, und stellt ein ```IDataChannel``` -Objekt bereit, das zum Senden und Empfangen von Daten über diesen Kanal verwendet werden kann.

So registrieren Sie einen Listener für das ```OnDataChannelCreated``` Ereignis:
```cpp
m_onDataChannelCreatedEventRevoker = m_remoteContext.OnDataChannelCreated(winrt::auto_revoke,
    [this](const IDataChannel& dataChannel, uint8_t channelId)
    {
        std::lock_guard lock(m_customDataChannelLock);
        m_customDataChannel = dataChannel;

        // Register to OnDataReceived and OnClosed event of the data channel here, see below...
    });
```

Um benachrichtigt zu werden, wenn Daten empfangen werden, registrieren Sie sich beim ```OnDataReceived``` -Ereignis für das ```IDataChannel``` objekt, das vom Handler bereitgestellt ```OnDataChannelCreated``` wird. Registrieren Sie sich für das ```OnClosed``` Ereignis, um benachrichtigt zu werden, wenn der Datenkanal geschlossen wurde.

```cpp
m_customChannelDataReceivedEventRevoker = m_customDataChannel.OnDataReceived(winrt::auto_revoke, 
    [this]()
    {
        // React on data received via the custom data channel here.
    });

m_customChannelClosedEventRevoker = m_customDataChannel.OnClosed(winrt::auto_revoke,
    [this]()
    {
        // React on data channel closed here.

        std::lock_guard lock(m_customDataChannelLock);
        if (m_customDataChannel)
        {
            m_customDataChannel = nullptr;
        }
    });
```

## <a name="sending-data"></a>Senden von Daten

Verwenden Sie die -Methode, um Daten über einen benutzerdefinierten Datenkanal zu ```IDataChannel::SendData()``` senden. Der erste Parameter ist ein ```winrt::array_view<const uint8_t>``` für die Daten, die gesendet werden sollen. Der zweite Parameter gibt an, wo die Daten erneut gesendet werden sollen, bis die andere Seite den Empfang bestätigt. 

>[!IMPORTANT]
>Bei schlechten Netzwerkbedingungen kann dasselbe Datenpaket mehr als einmal eingehen. Der empfangende Code muss in der Lage sein, diese Situation zu behandeln.

```cpp
uint8_t data[] = {1};
m_customDataChannel.SendData(data, true);
```

## <a name="closing-a-custom-data-channel"></a>Schließen eines benutzerdefinierten Datenkanals

Um einen benutzerdefinierten Datenkanal zu schließen, verwenden Sie die ```IDataChannel::Close()``` -Methode. Beide Seiten werden durch das -Ereignis benachrichtigt, ```OnClosed``` sobald der benutzerdefinierte Datenkanal geschlossen wurde.

```cpp
m_customDataChannel.Close();
```

## <a name="see-also"></a>Weitere Informationen
* [Schreiben einer Holographic Remoting-Remote-App mit Windows Mixed Reality-APIs](holographic-remoting-create-remote-wmr.md)
* [Schreiben einer Holographic Remoting-Remote-App mit OpenXR-APIs](holographic-remoting-create-remote-openxr.md)
* [Schreiben einer benutzerdefinierten Holographic Remoting Player-App](holographic-remoting-create-player.md)
* [Problembehandlung und Einschränkungen für Holographic Remoting](holographic-remoting-troubleshooting.md)
* [Holographic Remoting-Software – Lizenzbedingungen](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Datenschutzerklärung von Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)