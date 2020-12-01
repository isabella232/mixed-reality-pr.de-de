---
title: Benutzerdefinierte Holographic Remoting-Datenkanäle
description: Benutzerdefinierte Datenkanäle können verwendet werden, um Benutzerdaten über die bereits festgelegte Holographic Remoting-Verbindung zu senden.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: Hololens, Remoting, Holographic Remoting, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Datenkanäle
ms.openlocfilehash: 119a08a7f0e41aca694184879e33aaf54160220c
ms.sourcegitcommit: 9664bcc10ed7e60f7593f3a7ae58c66060802ab1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/01/2020
ms.locfileid: "96443451"
---
# <a name="custom-holographic-remoting-data-channels"></a>Benutzerdefinierte Holographic Remoting-Datenkanäle

>[!NOTE]
>Diese Anleitung gilt speziell für Holographic-Remoting auf hololens 2.

Verwenden Sie benutzerdefinierte Datenkanäle, um benutzerdefinierte Daten über eine festgelegte remotingverbindung zu senden.

>[!IMPORTANT]
>Benutzerdefinierte Datenkanäle erfordern eine benutzerdefinierte Remote-app und eine benutzerdefinierte Player-App, da Sie die Kommunikation zwischen den beiden benutzerdefinierten Apps ermöglicht.

>[!TIP]
>Ein einfaches Ping-Pong-Beispiel finden Sie im [GitHub-Repository für Holographic-Remoting-Beispiele](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)in den Remote-und Player-Beispielen. Heben Sie die Auskommentierung ```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE``` in den Dateien sampleremotemain. h/sampleplayermain. h auf, um den Beispielcode zu aktivieren.


## <a name="create-a-custom-data-channel"></a>Erstellen eines benutzerdefinierten Daten Kanals


Zum Erstellen eines benutzerdefinierten Daten Kanals sind die folgenden Felder erforderlich:
```cpp
std::recursive_mutex m_customDataChannelLock;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel m_customDataChannel = nullptr;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnDataReceived_revoker m_customChannelDataReceivedEventRevoker;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnClosed_revoker m_customChannelClosedEventRevoker;
```

Nachdem eine Verbindung hergestellt wurde, kann die Erstellung neuer Datenkanäle entweder von der Remote Seite und/oder von der Player Seite initiiert werden. Sowohl remotecontext als auch playercontext stellen hierfür eine- ```CreateDataChannel()``` Methode bereit. Der erste Parameter ist die Kanal-ID, die verwendet wird, um den Datenkanal in nachfolgenden Vorgängen zu identifizieren. Der zweite Parameter ist die Priorität, die die Priorität angibt, mit der Daten dieses Kanals auf die andere Seite übertragen werden. Der gültige Bereich für Channel-IDs ist 0 bis einschließlich 63 für die Remote Seite und 64 bis einschließlich 127 für die Player Seite. Gültige Prioritäten sind ```Low``` ```Medium``` oder ```High``` (auf beiden Seiten).

So initiieren Sie die Erstellung eines Daten Kanals auf der **Remote** Seite:
```cpp
// Valid channel ids for channels created on the remote side are 0 up to and including 63
m_remoteContext.CreateDataChannel(0, DataChannelPriority::Low);
```

So initiieren Sie die Erstellung eines Daten Kanals auf der **Player** Seite:
```cpp
// Valid channel ids for channels created on the player side are 64 up to and including 127
m_playerContext.CreateDataChannel(64, DataChannelPriority::Low);
```

>[!NOTE]
>Zum Erstellen eines neuen benutzerdefinierten Daten Kanals muss nur eine Seite (Remote oder Player) die-Methode aufruft ```CreateDataChannel``` .

## <a name="handling-custom-data-channel-events"></a>Behandeln von benutzerdefinierten Datenkanal Ereignissen

Zum Einrichten eines benutzerdefinierten Daten Kanals ```OnDataChannelCreated``` muss das Ereignis behandelt werden (sowohl auf dem Player als auch auf der Remote Seite). Es wird ausgelöst, wenn ein Benutzerdaten Kanal von beiden Seiten erstellt wurde, und stellt ein- ```IDataChannel``` Objekt bereit, das zum Senden und empfangen von Daten über diesen Kanal verwendet werden kann.

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

Um beim Empfang von Daten benachrichtigt zu werden, registrieren Sie sich für das- ```OnDataReceived``` Ereignis für das ```IDataChannel``` vom-Handler bereitgestellte Objekt ```OnDataChannelCreated``` . Registrieren Sie sich für das ```OnClosed``` Ereignis, um benachrichtigt zu werden, wenn der Datenkanal geschlossen wurde.

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

Verwenden Sie die-Methode, um Daten über einen benutzerdefinierten Datenkanal zu senden ```IDataChannel::SendData()``` . Der erste Parameter ist ein-Wert ```winrt::array_view<const uint8_t>``` für die Daten, die gesendet werden sollen. Der zweite Parameter gibt an, wohin die Daten erneut gesendet werden sollen, bis die andere Seite den Empfang bestätigt. 

>[!IMPORTANT]
>Im Falle fehlerhafter Netzwerkbedingungen kann das gleiche Datenpaket mehrmals eintreffen. Der empfangende Code muss in der Lage sein, diese Situation zu verarbeiten.

```cpp
uint8_t data[] = {1};
m_customDataChannel.SendData(data, true);
```

## <a name="closing-a-custom-data-channel"></a>Schließen eines benutzerdefinierten Daten Kanals

Verwenden Sie die-Methode, um einen benutzerdefinierten Datenkanal zu schließen ```IDataChannel::Close()``` . Beide Seiten werden durch das Ereignis benachrichtigt, ```OnClosed``` sobald der benutzerdefinierte Datenkanal geschlossen wurde.

```cpp
m_customDataChannel.Close();
```

## <a name="see-also"></a>Weitere Informationen
* [Schreiben einer Holographic Remoting-Remote-App mithilfe gemischter Windows-APIs](holographic-remoting-create-remote-wmr.md)
* [Schreiben einer Holographic Remoting-Remote-App mithilfe von openxr-APIs](holographic-remoting-create-remote-openxr.md)
* [Schreiben einer benutzerdefinierten Holographic Remoting Player-App](holographic-remoting-create-player.md)
* [Problembehandlung und Einschränkungen für Holographic Remoting](holographic-remoting-troubleshooting.md)
* [Holographic Remoting-Software – Lizenzbedingungen](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Datenschutzerklärung von Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)
