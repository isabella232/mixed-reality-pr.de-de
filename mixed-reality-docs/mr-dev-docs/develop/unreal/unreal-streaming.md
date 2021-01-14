---
title: Streaming in Unreal
description: Erfahren Sie, wie Sie Ihre Unreal-Apps auf HoloLens 2 streamen können, einschließlich Einschränkungen und Befehlszeilenoptionen für das Streaming.
author: sw5813
ms.author: suwu
ms.date: 12/7/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Streaming, PC, Holographic Remoting in Apps, Holographic Remoting Player, Dokumentation, Mixed Reality-Headset Windows Mixed Reality-Headset, Virtual Reality-Headset
appliesto:
- HoloLens
- HoloLens 2
ms.openlocfilehash: a0c376ed6366e57b8a521c52db2fc02fcd1c0285
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009950"
---
# <a name="streaming-in-unreal"></a>Streaming in Unreal

Das Streamen von einem PC zu HoloLens bietet hauptsächlich zwei Vorteile: 
* Es ermöglicht Ihrer Mixed Reality-App die Nutzung der Rechenleistung Ihres PCs. 
* Es verkürzt die Iterationszeiten bei der Entwicklung. 

Für den Einstieg müssen Sie den [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) auf Ihr HoloLens-Gerät herunterladen. Durch den Holographic Remoting-Player kann Ihre App direkt aus den folgenden Quellen zum Remoteplayer auf Ihrer HoloLens streamen:

* dem Unreal Engine-Editor
* einer verpackten Windows-Programmdatei 

Beim Streamen haben Sie Zugriff auf nahezu alle der HoloLens-Funktionen, die Ihnen auch beim Ausführen einer Anwendung auf einem Gerät zur Verfügung stehen. Dies schließt [Handgelenksnachverfolgung](unreal-hand-tracking.md) (bei einer HoloLens 2), [Räumliche Abbildung](unreal-spatial-mapping.md) und [Raumanker](unreal-spatial-anchors.md) (Spatial Anchors) ein, die Funktionen in dieser [Liste](../platform-capabilities-and-apis/holographic-remoting-troubleshooting.md) sind jedoch ausgenommen. 

> [!NOTE]
> * Die Streamingqualität hängt stark von der Feldstärke Ihres WLAN-Netzwerks ab.
> * Alle Funktionen werden automatisch für den Holographic Remoting Player aktiviert. Wenn Sie auf eine Funktion stoßen, die per Streaming nur mit einer Benutzerberechtigung arbeitet, diese bei Ausführung auf dem Gerät aber nicht benötigt (Beispiel: Eye Tracking), vergewissern Sie sich in den Projekteinstellungen, dass Sie die richtigen Funktionen aktiviert haben.

### <a name="streaming-limitations"></a>Streamingeinschränkungen

Hand-Meshes, die HoloLens-Kamera und die Systemtastatur sind per Streaming nicht verfügbar. Beachten Sie, dass Spracheingaben für gestreamte Apps über das Mikrofon des PCs abgerufen werden können, von dem aus Sie streamen.

#### <a name="openxr"></a>OpenXR

Unreal 4.26 unterstützt bei Ausführung in OpenXR das Streaming auf die Versionen 2.4.0+ des Holographic Remoting-Players. Bei OpenXR-Streaming in 2.4.0 fehlt die Unterstützung für räumliche Abbildung und Spatial Anchors. 

## <a name="device-support"></a>Geräteunterstützung

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Quelle</strong></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens (1. Generation)</strong></a></td>
        <td><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></td>
        <td><strong>Immersive Headsets</strong></td>
    </tr>
     <tr>
        <td>Unreal-Editor</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
    <tr>
        <td>Windows-Paket</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>

</table>

## <a name="streaming-from-the-unreal-editor"></a>Streaming vom Unreal-Editor

Als Entwickler werden Sie feststellen, dass das Streaming vom Unreal-Editor zu Ihrem HoloLens-Gerät beim Testen signifikante Vorteile bietet, nämlich dass Sie nicht mehr auf das Erstellen und Bereitstellen Ihrer App warten müssen, bevor Sie Ihre Updates ausprobieren.

Im unserer Tutorialreihe finden Sie ausführliche Anweisungen zum [Streamen aus dem Unreal-Editor](tutorials/unreal-uxt-ch6.md#device-only-streaming).

## <a name="streaming-from-a-packaged-windows-executable"></a>Streamen von einer verpackten Windows-Programmdatei

Seit Unreal 4.25.1 können Sie Ihre App aus einer verpackten Windows-Programmdatei zu einem HoloLens 2-Gerät streamen: 

1. Wechseln Sie im Editormenü zu **Datei > Paketprojekt > Windows**. 
    * Wählen Sie einen Speicherort aus, um Ihr Paket zu speichern, und wählen Sie **Ordner auswählen** aus.

2. Nachdem das Erstellen des Pakets abgeschlossen wurde, öffnen Sie den **Holographic Remoting Player** auf Ihrer HoloLens 2, und notieren Sie die IP-Adresse. 
3. Lassen Sie den **Holographic Remoting Player** geöffnet, und verwenden Sie die Eingabeaufforderung zum: 
    * Wechseln in das lokale Verzeichnis, in dem Sie das Paket gespeichert haben.
    * Geben Sie den folgenden Befehl ein: `<App Name>.exe -vr -HoloLensRemoting=<IP Address>`

> [!NOTE]
> Der Anwendungsname in Ihren Projekteinstellungen sollte automatisch zum Erstellen des Windows-Pakets verwendet werden. Wenn diese aus irgendeinem Grund verschieden sind, verwenden Sie den Namen der Windows-Programmdatei in der Eingabeaufforderung.

Drücken Sie die EINGABETASTE, und sehen Sie, wie das Streamen Ihrer Anwendung beginnt!

### <a name="command-line-options"></a>Befehlszeilenoptionen

Zusätzliche Befehlszeilenoptionen für das Streaming von jeder Plattform in Unreal Engine 4.26+ finden Sie in der Tabelle unten. 

[!INCLUDE[](includes/tabs-streaming-args.md)]

## <a name="see-also"></a>Siehe auch

* [Holographic Remoting: Versionsverlauf](../platform-capabilities-and-apis/holographic-remoting-version-history.md)
* [Schreiben einer benutzerdefinierten Holographic Remoting Player-App](../platform-capabilities-and-apis/holographic-remoting-create-player.md)
* [Einrichten einer sicheren Verbindung mit Holographic Remoting](../platform-capabilities-and-apis/holographic-remoting-secure-connection.md)
