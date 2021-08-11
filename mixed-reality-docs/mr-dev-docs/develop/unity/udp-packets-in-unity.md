---
title: UDP-Pakete in Unity-UWP-Apps
description: Erfahren Sie, wie Sie eine Unity-UWP-App einrichten, um UDP-Pakete über ein sicheres Netzwerk zu senden und zu empfangen.
author: hferrone
ms.author: v-hferrone
ms.date: 02/3/2021
ms.topic: article
keywords: UDP, UWP, Unity, UDP-Pakete, Socket, Clientserver, Endpunkt, Netzwerk, Remotecomputer, Datagramsocket, Beispiel, .NET
ms.openlocfilehash: a24498384ccb2018f62f00523bf33764d2ef7c019dec0cfd8fc70d86b55a81bb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115192556"
---
# <a name="udp-packets-in-unity-uwp-apps"></a>UDP-Pakete in Unity-UWP-Apps

Sie können Ihre UWP-Unity-Apps (Universal Windows Platform) einrichten, um UDP-Pakete mithilfe eines UDP-Socketclients und -Servers zu empfangen. UDP-Sockets verwalten keine Verbindung auf beiden Endpunkten, sodass sie eine schnelle und einfache Lösung für netzwerke zwischen Remotecomputern sind. Sie sind jedoch dafür verantwortlich, zu überprüfen, ob die Pakete an ihr Ziel gelangen, da UDP-Sockets dies nicht automatisch tun.

## <a name="setup"></a>Setup

Öffnen Sie Ihre Projekte HoloLens manifest.jsin der Datei, und stellen Sie sicher, dass Sie Aktiviert haben:
* **Internet (Client & Server)** 
* **Private Netzwerke (Client & Server)**.

## <a name="build-your-socket-client-and-server"></a>Erstellen ihres Socketclients und -servers 

Befolgen Sie die Anweisungen zum [Erstellen eines grundlegenden UDP-Socketclients und -Servers.](/windows/uwp/networking/sockets#build-a-basic-udp-socket-client-and-server) Sie verwenden die [DatagramSocket-Klasse,](/uwp/api/Windows.Networking.Sockets.DatagramSocket) um Daten über UDP zu senden und zu empfangen und einen Echoclient und -server zu bilden. Es wird auch empfohlen, die anderen Ressourcenabschnitte in diesem Artikel zu lesen, da sie für angepasstere und komplexere Anwendungsfälle gelten. 

> [!IMPORTANT]
> Wenn Sie Probleme beim Senden von UDP-Paketen vom PC an den PC haben, überprüfen Sie, ob Ihr Netzwerk diese Vorgänge zulässt. Wenn Ihr Netzwerk die UDP-Pakete in irgendeiner Weise blockiert, kann Ihr HoloLens Gerät nicht darauf lauschen.

Sie können eine vollständige DatagramSocket-UDP-Beispiel-App über den folgenden Link herunterladen:

> [!div class="nextstepaction"]
> [Installieren der Tools](/samples/microsoft/windows-universal-samples/datagramsocket/)

## <a name="see-also"></a>Siehe auch 
* [Experimente mit freigegebenen Hologramme und Azure Blob Storage/UDP Multicasting](https://mtaulty.com/2017/12/29/experiments-with-shared-holograms-and-azure-blob-storage-udp-multicasting-part-1/)