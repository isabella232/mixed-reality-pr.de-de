---
ms.openlocfilehash: 212aa75ae91a7beebbfa609af6cc47106ba34b55
ms.sourcegitcommit: 0509cf6c57067cffd75a0189106e3369e9ecc5c8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96855881"
---
# <a name="windows-mixed-reality"></a>[<span data-ttu-id="9d9e6-101">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="9d9e6-101">Windows Mixed Reality</span></span>](#tab/wmr)

| <span data-ttu-id="9d9e6-102">Option</span><span class="sxs-lookup"><span data-stu-id="9d9e6-102">Option</span></span> | <span data-ttu-id="9d9e6-103">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9d9e6-103">Description</span></span> |
| ------ | ----------- |
| `-HoloLensRemoting=<IP address:port>` | <span data-ttu-id="9d9e6-104">Nimmt die IP-Adresse (und optional den Port) des HoloLens 2-Geräts an, mit dem eine Verbindung hergestellt werden soll.</span><span class="sxs-lookup"><span data-stu-id="9d9e6-104">Takes the IP address (and optional port) of the HoloLens 2 device to connect to.</span></span> <span data-ttu-id="9d9e6-105">Wenn kein Port angegeben wird, wird standardmäßig 8265 verwendet.</span><span class="sxs-lookup"><span data-stu-id="9d9e6-105">If no port is provided, default to 8265.</span></span> |
| `-RemotingBitrate=<bitrate>` | <span data-ttu-id="9d9e6-106">(optional) Standardwert 8000.</span><span class="sxs-lookup"><span data-stu-id="9d9e6-106">(optional) Default 8000.</span></span> <span data-ttu-id="9d9e6-107">Maximale Netzwerk-Übertragungsrate (KB/s).</span><span class="sxs-lookup"><span data-stu-id="9d9e6-107">Max network transfer rate (kb/s).</span></span> |
| `-HoloLensRemotingListen` | <span data-ttu-id="9d9e6-108">(optional) Startet einen Lauschserver</span><span class="sxs-lookup"><span data-stu-id="9d9e6-108">(optional) Start a listen server</span></span> |
| `-HoloLensRemotingListenPort=<port>` | <span data-ttu-id="9d9e6-109">(optional) Nimmt den Port an, an dem gelauscht werden soll.</span><span class="sxs-lookup"><span data-stu-id="9d9e6-109">(optional) Takes the port to listen on.</span></span> <span data-ttu-id="9d9e6-110">Wird zum Herstellen der Verbindung mit einem PC oder einer VM von einem HoloLens-Gerät verwendet.</span><span class="sxs-lookup"><span data-stu-id="9d9e6-110">Used for connecting to a PC or VM from a HoloLens device.</span></span> |
| `-HoloLens1Remoting=<IP address>` | <span data-ttu-id="9d9e6-111">(in 4.26 veraltet) Nimmt die IP-Adresse des HoloLens 1-Geräts an, mit dem die Verbindung erfolgen soll</span><span class="sxs-lookup"><span data-stu-id="9d9e6-111">(deprecated in 4.26) Takes the IP address of the HoloLens 1 device to connect to</span></span> |

# <a name="openxr"></a>[<span data-ttu-id="9d9e6-112">OpenXR</span><span class="sxs-lookup"><span data-stu-id="9d9e6-112">OpenXR</span></span>](#tab/openxr)

| <span data-ttu-id="9d9e6-113">Option</span><span class="sxs-lookup"><span data-stu-id="9d9e6-113">Option</span></span> | <span data-ttu-id="9d9e6-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9d9e6-114">Description</span></span> |
| ------ | ----------- |
| `-HoloLensRemoting=<IP address:port or port>` | <span data-ttu-id="9d9e6-115">Nimmt die IP-Adresse (und optional den Port, Standardwert 8265) des HoloLens 2-Geräts an, mit dem die Verbindung erfolgen soll, oder den Port, an dem die App auf Verbindungen lauschen soll.</span><span class="sxs-lookup"><span data-stu-id="9d9e6-115">Takes the IP address (and optional port, default 8265) of the HoloLens 2 device to connect to, or the port on which the app should listen on for connections.</span></span> |
| `-EnableAudio` | <span data-ttu-id="9d9e6-116">(optional) Beim Remoting Audiodaten vom PC verwenden</span><span class="sxs-lookup"><span data-stu-id="9d9e6-116">(optional) Use audio from PC when remoting</span></span>  |
| `-Listen` | <span data-ttu-id="9d9e6-117">(optional) Startet einen Lauschserver</span><span class="sxs-lookup"><span data-stu-id="9d9e6-117">(optional) Start a listen server</span></span> |
| `-RemotingBitrate=<bitrate>` | <span data-ttu-id="9d9e6-118">(optional) Standardwert 8000.</span><span class="sxs-lookup"><span data-stu-id="9d9e6-118">(optional) Default 8000.</span></span> <span data-ttu-id="9d9e6-119">Maximale Netzwerk-Übertragungsrate (KB/s).</span><span class="sxs-lookup"><span data-stu-id="9d9e6-119">Max network transfer rate (kb/s).</span></span> |
| `-RemotingCodec=<codec>` | <span data-ttu-id="9d9e6-120">(Optional) Verbindungscodec</span><span class="sxs-lookup"><span data-stu-id="9d9e6-120">(optional) Connection codec</span></span>  |