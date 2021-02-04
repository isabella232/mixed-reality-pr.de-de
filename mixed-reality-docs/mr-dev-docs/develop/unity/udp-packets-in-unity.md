---
title: UDP-Pakete in Unity-UWP-apps
description: Erfahren Sie, wie Sie eine Unity-UWP-App einrichten, um UDP-Pakete über ein sicheres Netzwerk zu senden und zu empfangen.
author: hferrone
ms.author: v-hferrone
ms.date: 02/3/2021
ms.topic: article
keywords: UDP, UWP, Unity, UDP-Pakete, Socket, Client Server, Endpunkt, Netzwerk, Remote Computer, DatagramSocket, Sample, .net
ms.openlocfilehash: e4fbdc12a1f7fbca44e14f6ace89ef791a09608f
ms.sourcegitcommit: 8647702638f7600c51df1d89d76c761b52bdf0d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/04/2021
ms.locfileid: "99566977"
---
# <a name="udp-packets-in-unity-uwp-apps"></a>UDP-Pakete in Unity-UWP-apps

Sie können ihre universelle Windows-Plattform (UWP) Unity-apps einrichten, um UDP-Pakete mithilfe eines UDP-socketclients und-Servers zu empfangen. UDP-Sockets behalten keine Verbindung auf beiden Endpunkten bei, sodass Sie eine schnelle und einfache Lösung für das Netzwerk zwischen Remote Computern sind. Allerdings sind Sie dafür verantwortlich, zu überprüfen, ob die Pakete an Ihr Ziel gelangen, da UDP-Sockets dies nicht automatisch durchführen.

## <a name="setup"></a>Einrichten

Öffnen Sie die Projekt hololens manifest.jsDatei, und stellen Sie sicher, dass Sie Folgendes aktiviert haben:
* **Internet (Client & Server)** 
* **Private Netzwerke (Client & Server)**.

## <a name="build-your-socket-client-and-server"></a>Erstellen Sie den socketclient und-Server. 

Befolgen Sie die Anweisungen zum [Aufbau eines grundlegenden UDP-socketclients und-Servers](https://docs.microsoft.com/windows/uwp/networking/sockets#build-a-basic-udp-socket-client-and-server). Sie verwenden die [DatagramSocket](https://docs.microsoft.com/uwp/api/Windows.Networking.Sockets.DatagramSocket) -Klasse, um Daten über UDP zu senden und zu empfangen und einen Echo-Client und-Server zu bilden. Außerdem wird empfohlen, die anderen Ressourcen Abschnitte in diesem Artikel zu lesen, da Sie für benutzerdefinierte und komplexere Anwendungsfälle gelten. 

> [!IMPORTANT]
> Wenn Sie Probleme beim Senden von UDP-Paketen vom PC an den PC haben, überprüfen Sie, ob Ihr Netzwerk diese Vorgänge zulässt. Wenn Ihr Netzwerk die UDP-Pakete in irgendeiner Weise blockiert, kann Ihr hololens-Gerät nicht darauf warten.

Sie können eine komplette DatagramSocket-UDP-Beispiel-App über den folgenden Link herunterladen:

> [!div class="nextstepaction"]
> [Installieren der Tools](https://docs.microsoft.com/samples/microsoft/windows-universal-samples/datagramsocket/)

## <a name="see-also"></a>Siehe auch 
* [Experimente mit freigegebenen Hologrammen und Azure BLOB Storage/UDP-Multicasting](https://mtaulty.com/2017/12/29/experiments-with-shared-holograms-and-azure-blob-storage-udp-multicasting-part-1/)