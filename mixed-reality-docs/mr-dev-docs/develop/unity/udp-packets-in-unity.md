---
title: UDP-Pakete in Unity-UWP-apps
description: Erfahren Sie, wie Sie eine Unity-UWP-App einrichten, um UDP-Pakete über ein sicheres Netzwerk zu senden und zu empfangen.
author: hferrone
ms.author: v-hferrone
ms.date: 02/3/2021
ms.topic: article
keywords: UDP, UWP, Unity, UDP-Pakete, Socket, Client Server, Endpunkt, Netzwerk, Remote Computer, DatagramSocket, Sample, .net
ms.openlocfilehash: b38897f228a62abeb63b7e2ffc0f2a98a840b781
ms.sourcegitcommit: ac315c1d35f2b9c431e79bc3f1212215301bb867
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/25/2021
ms.locfileid: "105550520"
---
# <a name="udp-packets-in-unity-uwp-apps"></a><span data-ttu-id="d79d7-104">UDP-Pakete in Unity-UWP-apps</span><span class="sxs-lookup"><span data-stu-id="d79d7-104">UDP packets in Unity UWP apps</span></span>

<span data-ttu-id="d79d7-105">Sie können ihre universelle Windows-Plattform (UWP) Unity-apps einrichten, um UDP-Pakete mithilfe eines UDP-socketclients und-Servers zu empfangen.</span><span class="sxs-lookup"><span data-stu-id="d79d7-105">You can setup your Universal Windows Platform (UWP) Unity apps to receive UDP packets with the help of a UDP socket client and server.</span></span> <span data-ttu-id="d79d7-106">UDP-Sockets behalten keine Verbindung auf beiden Endpunkten bei, sodass Sie eine schnelle und einfache Lösung für das Netzwerk zwischen Remote Computern sind.</span><span class="sxs-lookup"><span data-stu-id="d79d7-106">UDP sockets don't maintain connection on both endpoints, so they're a fast and simple solution for networking between remote machines.</span></span> <span data-ttu-id="d79d7-107">Allerdings sind Sie dafür verantwortlich, zu überprüfen, ob die Pakete an Ihr Ziel gelangen, da UDP-Sockets dies nicht automatisch durchführen.</span><span class="sxs-lookup"><span data-stu-id="d79d7-107">However, you'll be responsible for checking if the packets get to their destination, as UDP sockets don't do that automatically.</span></span>

## <a name="setup"></a><span data-ttu-id="d79d7-108">Einrichten</span><span class="sxs-lookup"><span data-stu-id="d79d7-108">Setup</span></span>

<span data-ttu-id="d79d7-109">Öffnen Sie die Projekt hololens manifest.jsDatei, und stellen Sie sicher, dass Sie Folgendes aktiviert haben:</span><span class="sxs-lookup"><span data-stu-id="d79d7-109">Open your projects HoloLens manifest.json file and make sure you've enabled:</span></span>
* <span data-ttu-id="d79d7-110">**Internet (Client & Server)**</span><span class="sxs-lookup"><span data-stu-id="d79d7-110">**Internet (Client & Server)**</span></span> 
* <span data-ttu-id="d79d7-111">**Private Netzwerke (Client & Server)**.</span><span class="sxs-lookup"><span data-stu-id="d79d7-111">**Private Networks (Client & Server)**.</span></span>

## <a name="build-your-socket-client-and-server"></a><span data-ttu-id="d79d7-112">Erstellen Sie den socketclient und-Server.</span><span class="sxs-lookup"><span data-stu-id="d79d7-112">Build your socket client and server</span></span> 

<span data-ttu-id="d79d7-113">Befolgen Sie die Anweisungen zum [Aufbau eines grundlegenden UDP-socketclients und-Servers](/windows/uwp/networking/sockets#build-a-basic-udp-socket-client-and-server).</span><span class="sxs-lookup"><span data-stu-id="d79d7-113">Follow the instructions for [building a basic UDP socket client and server](/windows/uwp/networking/sockets#build-a-basic-udp-socket-client-and-server).</span></span> <span data-ttu-id="d79d7-114">Sie verwenden die [DatagramSocket](/uwp/api/Windows.Networking.Sockets.DatagramSocket) -Klasse, um Daten über UDP zu senden und zu empfangen und einen Echo-Client und-Server zu bilden.</span><span class="sxs-lookup"><span data-stu-id="d79d7-114">You'll be using the [DatagramSocket](/uwp/api/Windows.Networking.Sockets.DatagramSocket) class to send and receive data over UDP and form an echo client and server.</span></span> <span data-ttu-id="d79d7-115">Außerdem wird empfohlen, die anderen Ressourcen Abschnitte in diesem Artikel zu lesen, da Sie für benutzerdefinierte und komplexere Anwendungsfälle gelten.</span><span class="sxs-lookup"><span data-stu-id="d79d7-115">We also recommend reading through the other resource sections in this article, as they apply to more customized and complex use cases.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="d79d7-116">Wenn Sie Probleme beim Senden von UDP-Paketen vom PC an den PC haben, überprüfen Sie, ob Ihr Netzwerk diese Vorgänge zulässt.</span><span class="sxs-lookup"><span data-stu-id="d79d7-116">If you're having trouble sending UDP packets from PC to PC, check that your network allows these operations.</span></span> <span data-ttu-id="d79d7-117">Wenn Ihr Netzwerk die UDP-Pakete in irgendeiner Weise blockiert, kann Ihr hololens-Gerät nicht darauf warten.</span><span class="sxs-lookup"><span data-stu-id="d79d7-117">If your network is blocking the UDP packets in any way, your HoloLens device won't be able to listen for them.</span></span>

<span data-ttu-id="d79d7-118">Sie können eine komplette DatagramSocket-UDP-Beispiel-App über den folgenden Link herunterladen:</span><span class="sxs-lookup"><span data-stu-id="d79d7-118">You can download a complete DatagramSocket UDP sample app from the link below:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d79d7-119">Installieren der Tools</span><span class="sxs-lookup"><span data-stu-id="d79d7-119">Install the tools</span></span>](/samples/microsoft/windows-universal-samples/datagramsocket/)

## <a name="see-also"></a><span data-ttu-id="d79d7-120">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="d79d7-120">See also</span></span> 
* [<span data-ttu-id="d79d7-121">Experimente mit freigegebenen Hologrammen und Azure BLOB Storage/UDP-Multicasting</span><span class="sxs-lookup"><span data-stu-id="d79d7-121">Experiments with Shared Holograms and Azure Blob Storage/UDP Multicasting</span></span>](https://mtaulty.com/2017/12/29/experiments-with-shared-holograms-and-azure-blob-storage-udp-multicasting-part-1/)