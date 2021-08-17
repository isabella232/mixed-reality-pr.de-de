---
title: Benutzerdefinierte Holographic Remoting-Datenkanäle
description: Benutzerdefinierte Datenkanäle können verwendet werden, um Benutzerdaten über die bereits eingerichtete Holographic Remoting-Verbindung zu senden.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, Remoting, Holographic Remoting, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Datenkanäle
ms.openlocfilehash: 1adda10aa7792eaeab0ac32cb37d73dcfd2b58e6
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2021
ms.locfileid: "122184711"
---
# <a name="custom-holographic-remoting-data-channels-c"></a>Benutzerdefinierte Holographic Remoting-Datenkanäle (C++)

>[!NOTE]
>Diese Anleitung gilt speziell für Holographic Remoting HoloLens 2.

Verwenden Sie benutzerdefinierte Datenkanäle, um benutzerdefinierte Daten über eine eingerichtete Remotingverbindung zu senden.

>[!IMPORTANT]
>Benutzerdefinierte Datenkanäle erfordern eine benutzerdefinierte Remote-App und eine benutzerdefinierte Player-App, da sie die Kommunikation zwischen den beiden benutzerdefinierten Apps ermöglicht.

>[!TIP]
>Ein einfaches Ping-Pong-Beispiel finden Sie in den Remote- und Playerbeispielen im [GitHub-Repository für Holographic Remoting-Beispiele.](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples) Entfernen Sie die Auskommentierung in den ```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE``` Dateien SampleRemoteMain.h/SamplePlayerMain.h, um den Beispielcode zu aktivieren.


## <a name="create-a-custom-data-channel"></a>Erstellen eines benutzerdefinierten Datenkanals


Zum Erstellen eines benutzerdefinierten Datenkanals sind die folgenden Felder erforderlich:
```cpp
std::recursive_mutex m_customDataChannelLock;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel m_customDataChannel = nullptr;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnDataReceived_revoker m_customChannelDataReceivedEventRevoker;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnClosed_revoker m_customChannelClosedEventRevoker;
```

Nachdem eine Verbindung erfolgreich hergestellt wurde, können Sie neue Datenkanäle von der Remoteseite, der Playerseite oder von beiden erstellen. Sowohl RemoteContext als auch PlayerContext stellen eine Methode ```CreateDataChannel()``` zum Erstellen von Datenkanälen zur Verfügung. Der erste Parameter ist die Kanal-ID, mit der der Datenkanal in nachfolgenden Vorgängen identifiziert wird. Der zweite Parameter ist die Priorität, die die Priorität angibt, mit der Daten dieses Kanals auf die andere Seite übertragen werden. Gültige Kanal-IDs auf der Remoteseite sind von 0 bis einschließlich 63 und 64 bis einschließlich 127 für die Spielerseite. Gültige Prioritäten sind ```Low``` ```Medium``` , oder ```High``` (auf beiden Seiten).

So starten Sie die Erstellung eines Datenkanals auf **der Remoteseite:**
```cpp
// Valid channel ids for channels created on the remote side are 0 up to and including 63
m_remoteContext.CreateDataChannel(0, DataChannelPriority::Low);
```

So starten Sie die Erstellung eines Datenkanals auf **playerseitiger** Seite:
```cpp
// Valid channel ids for channels created on the player side are 64 up to and including 127
m_playerContext.CreateDataChannel(64, DataChannelPriority::Low);
```

>[!NOTE]
>Um einen neuen benutzerdefinierten Datenkanal zu erstellen, muss nur eine Seite (remote oder player) die -Methode ```CreateDataChannel``` aufrufen.

## <a name="handling-custom-data-channel-events"></a>Behandeln von benutzerdefinierten Datenkanalereignissen

Um einen benutzerdefinierten Datenkanal zu erstellen, muss das Ereignis verarbeitet werden (sowohl auf der Player- als auch ```OnDataChannelCreated``` auf der Remoteseite). Er wird ausgelöst, wenn ein Benutzerdatenkanal von beiden Seiten erstellt wurde, und stellt ein -Objekt zur Verwendung zum Senden und Empfangen von Daten ```IDataChannel``` über diesen Kanal zur Verwendung.

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

Um benachrichtigt zu werden, wenn Daten empfangen werden, registrieren Sie sich für das -Ereignis für das ```OnDataReceived``` ```IDataChannel``` vom Handler bereitgestellte ```OnDataChannelCreated``` -Objekt. Registrieren Sie sich ```OnClosed``` für das Ereignis, um benachrichtigt zu werden, wenn der Datenkanal geschlossen wurde.

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

Verwenden Sie die -Methode, um Daten über einen benutzerdefinierten Datenkanal ```IDataChannel::SendData()``` zu senden. Der erste Parameter ist ein ```winrt::array_view<const uint8_t>``` für die Daten, die gesendet werden sollen. Der zweite Parameter gibt an, wo die Daten erneut senden werden sollen, bis die andere Seite den Empfang bestätigt. 

>[!IMPORTANT]
>Bei schlechten Netzwerkbedingungen kann dasselbe Datenpaket mehr als einmal eintreffen. Der empfangende Code muss in der Lage sein, diese Situation zu behandeln.

```cpp
uint8_t data[] = {1};
m_customDataChannel.SendData(data, true);
```

## <a name="closing-a-custom-data-channel"></a>Schließen eines benutzerdefinierten Datenkanals

Verwenden Sie die -Methode, um einen benutzerdefinierten Datenkanal ```IDataChannel::Close()``` zu schließen. Beide Seiten werden vom Ereignis benachrichtigt, ```OnClosed``` sobald der benutzerdefinierte Datenkanal geschlossen wurde.

```cpp
m_customDataChannel.Close();
```

## <a name="see-also"></a>Weitere Informationen
* [Übersicht über Holographic Remoting](holographic-remoting-overview.md)
* [Schreiben einer Holographic Remoting-Remote-App mithilfe Windows Mixed Reality APIs](holographic-remoting-create-remote-wmr.md)
* [Schreiben einer Holographic Remoting-Remote-App mit OpenXR-APIs](holographic-remoting-create-remote-openxr.md)
* [Schreiben einer benutzerdefinierten Holographic Remoting Player-App](holographic-remoting-create-player.md)
* [Problembehandlung und Einschränkungen bei Holographic Remoting](holographic-remoting-troubleshooting.md)
* [Holographic Remoting-Software – Lizenzbedingungen](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Datenschutzerklärung von Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)