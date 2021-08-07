---
title: Aktivieren des Platzierens von 3D-Modellen auf der Startseite
description: Erfahren Sie, wie Sie 3D-Modelle von Ihrer Website oder Anwendung in der Windows Mixed Reality-Startseite platzieren.
author: thmignon
ms.author: thmignon
ms.date: 05/04/2018
ms.topic: article
keywords: 3D, Modell, Ort zu Hause, Ort, Welt, Modellierung, Mixed Reality Startumgebung, Web, App, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 29761cb2a8725221a3be90187488cb13bf6643e4ff334a1edca73e633e7b1d4c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115186796"
---
# <a name="enable-placement-of-3d-models-in-the-mixed-reality-home"></a>Aktivieren der Platzierung von 3D-Modellen in der Mixed Reality Startumgebung

> [!NOTE]
> Dieses Feature wurde im Rahmen des [Windows 10 April 2018-Updates](/windows/mixed-reality/enthusiast-guide/release-notes-april-2018)hinzugefügt. Ältere Versionen von Windows sind mit diesem Feature nicht kompatibel.

Das [Windows Mixed Reality Home](../discover/navigating-the-windows-mixed-reality-home.md) ist der Ausgangspunkt, an dem Benutzer vor dem Starten von Anwendungen landen. In einigen Szenarien ermöglichen 2D-Apps (z. B. die Hologramme-App) die direkte Platzierung von 3D-Modellen im Mixed Reality Startumgebung als Verzierungen oder zur weiteren Überprüfung in vollständiger 3D. Mit dem *Add Model-Protokoll* können Sie ein 3D-Modell von Ihrer Website oder Anwendung direkt an die Windows Mixed Reality-Startseite senden, wo es wie [3D-App-Startprogramme,](3d-app-launcher-design-guidance.md)2D-Apps und Hologramme beibehalten wird. 

Wenn Sie z. B. eine Anwendung entwickeln, die einen Katalog mit 3D-Modellen zum Entwerfen eines Raums aufzeichnet, verwenden Sie das *Add Model-Protokoll,* damit Benutzer diese 3D-Modelle aus dem Katalog platzieren können. Nach der Platzierung auf der Welt können Benutzer diese 3D-Modelle wie andere Hologramme in der Startseite verschieben, ihre Größe ändern und entfernen. Dieser Artikel bietet eine Übersicht über die Implementierung des *Add-Model-Protokolls,* damit Benutzer ihre Welt mit 3D-Objekten aus Ihrer App oder dem Web ergänzen können.

## <a name="device-support"></a>Geräteunterstützung

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Feature</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
    </tr>
     <tr>
        <td>Modellprotokoll hinzufügen</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="the-basics"></a>Grundlagen

Es gibt zwei Schritte zum Aktivieren der Platzierung von 3D-Modellen im Windows Mixed Reality Home:
1. [Stellen Sie sicher, dass Ihr 3D-Modell mit der Windows Mixed Reality-Startseite kompatibel ist.](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
2. Implementieren Sie das *Add Model-Protokoll* in Ihrer Anwendung oder Webseite (dieser Artikel).

## <a name="implementing-the-add-model-protocol"></a>Implementieren des *Add-Model-Protokolls*

Sobald Sie über ein [kompatibles 3D-Modell](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)verfügen, können Sie das *Add Model-Protokoll* implementieren, indem Sie den folgenden URI von jeder Webseite oder Anwendung aktivieren:

```
ms-mixedreality:addmodel?uri=<Path to a .glb 3D model either local or remote>
```

Wenn der URI auf eine Remoteressource verweist, wird er automatisch heruntergeladen und in der Startseite platziert. Lokale Ressourcen werden in den App-Datenordner der Mixed Reality Startumgebung kopiert, bevor sie in der Startseite platziert werden. Es wird empfohlen, Ihre Benutzeroberfläche so zu entwerfen, dass Szenarien berücksichtigt werden, in denen der Benutzer möglicherweise eine ältere Version von Windows ausführt, die dieses Feature nicht unterstützt, indem die Schaltfläche ausgeblendet oder nach Möglichkeit deaktiviert wird. 

### <a name="invoking-the-add-model-protocol-from-a-universal-windows-platform-app"></a>Aufrufen des *Add Model-Protokolls* aus einer Universal Windows Platform-App:

```C#
private async void launchURI_Click(object sender, RoutedEventArgs e)
{
   // Define the add model URI
   var uriAddModel = new Uri(@"ms-mixedreality:addModel?uri=sample.glb");

   // Launch the URI to invoke the placement
   var success = await Windows.System.Launcher.LaunchUriAsync(uriAddModel);

   if (success)
   {
      // URI launched
   }
   else
   {
      // URI launch failed
   }
}
```

### <a name="invoking-the-add-model-protocol-from-a-webpage"></a>Aufrufen des *Add Model-Protokolls* von einer Webseite:

```html
<a class="btn btn-default" href="ms-mixedreality:addModel?uri=sample.glb"> Place 3D Model </a>
```

## <a name="considerations-for-immersive-vr-headsets"></a>Überlegungen zu immersiven Headsets (VR)

* Bei immersiven Headsets (VR) muss der Mixed Reality-Portal nicht ausgeführt werden, bevor das *Add Model Protocol (Modellprotokoll hinzufügen)* aufgerufen wird. In diesem Fall startet das *Add Model-Protokoll* die Mixed Reality-Portal und platzieren das Objekt direkt an der Stelle, an der das Headset nach dem Eintreffen im Mixed Reality Startumgebung sucht. 
* Stellen Sie beim Aufrufen des *Add Model-Protokolls* über den Desktop mit dem bereits ausgeführten Mixed Reality-Portal sicher, dass das Headset "aktiv" ist. Wenn nicht, ist die Platzierung nicht erfolgreich. 

## <a name="see-also"></a>Weitere Informationen

* [Erstellen von 3D-Modellen für die Verwendung im Windows Mixed Reality Home](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Navigieren auf der Startseite von Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md)