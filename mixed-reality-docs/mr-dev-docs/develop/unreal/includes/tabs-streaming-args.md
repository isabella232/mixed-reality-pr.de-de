---
ms.openlocfilehash: 212aa75ae91a7beebbfa609af6cc47106ba34b55
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2021
ms.locfileid: "96855881"
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