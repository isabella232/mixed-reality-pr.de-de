---
ms.openlocfilehash: 283ef0bedc96a63d34a66fa0d88dee97420957c7744ad3702c6ac3bc34c14310
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115218857"
---
# <a name="windows-mixed-reality"></a>[Windows Mixed Reality](#tab/wmr)

| Option | Beschreibung |
| ------ | ----------- |
| `-HoloLensRemoting=<IP address:port>` | Nimmt die IP-Adresse (und optional den Port) des HoloLens 2-Geräts an, mit dem eine Verbindung hergestellt werden soll. Wenn kein Port angegeben wird, wird standardmäßig 8265 verwendet. |
| `-RemotingBitrate=<bitrate>` | (optional) Standardwert 8000. Maximale Netzwerk-Übertragungsrate (KB/s). |
| `-HoloLensRemotingListen` | (optional) Startet einen Lauschserver |
| `-HoloLensRemotingListenPort=<port>` | (optional) Nimmt den Port an, an dem gelauscht werden soll. Wird zum Herstellen der Verbindung mit einem PC oder einer VM von einem HoloLens-Gerät verwendet. |
| `-HoloLens1Remoting=<IP address>` | (in 4.26 veraltet) Nimmt die IP-Adresse des HoloLens 1-Geräts an, mit dem die Verbindung erfolgen soll |

# <a name="openxr"></a>[OpenXR](#tab/openxr)

| Option | Beschreibung |
| ------ | ----------- |
| `-HoloLensRemoting=<IP address:port or port>` | Nimmt die IP-Adresse (und optional den Port, Standardwert 8265) des HoloLens 2-Geräts an, mit dem die Verbindung erfolgen soll, oder den Port, an dem die App auf Verbindungen lauschen soll. |
| `-EnableAudio` | (optional) Beim Remoting Audiodaten vom PC verwenden  |
| `-Listen` | (optional) Startet einen Lauschserver |
| `-RemotingBitrate=<bitrate>` | (optional) Standardwert 8000. Maximale Netzwerk-Übertragungsrate (KB/s). |
| `-RemotingCodec=<codec>` | (Optional) Verbindungscodec  |